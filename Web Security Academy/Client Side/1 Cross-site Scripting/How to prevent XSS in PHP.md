Parent Links : [[Cross-site scripting]] > [[How to prevent XSS attacks]]     

## How to prevent XSS in PHP
  
In PHP there is a built-in function to encode entities called `htmlentities`. You should call this function to escape your input when inside an HTML context. The function should be called with three arguments:  
>• Your input string.  
• `ENT_QUOTES`, which is a flag that specifies all quotes should be encoded.  
• The character set, which in most cases should be UTF-8.  
  
For example:  
```php 
<?php echo htmlentities($input, ENT_QUOTES, 'UTF-8');?>  
```  

When in a JavaScript string context, you need to Unicode-escape input as already described. Unfortunately, PHP doesn't provide an API to Unicode-escape a string. Here is some code to do that in PHP:  
```php
<?php           
                     function jsEscape($str) {  
               $output = '';  
               $str = str_split($str);  
               for($i=0;$i<count($str);$i++) {  
                $chrNum = ord($str[$i]);  
                $chr = $str[$i];  
                if($chrNum === 226) {  
                  if(isset($str[$i+1]) && ord($str[$i+1]) === 128) {  
                    if(isset($str[$i+2]) && ord($str[$i+2]) === 168) {  
                      $output .= '\u2028';  
                      $i += 2;  
                      continue;  
                    }  
                    if(isset($str[$i+2]) && ord($str[$i+2]) === 169) {  
                      $output .= '\u2029';  
                      $i += 2;  
                      continue;  
                    }  
                  }  
                }  
                switch($chr) {  
                  case "'":  
                  case '"':  
                  case "\n";  
                  case "\r";  
                  case "&";  
         case "\\";  
                  case "<":  
                  case ">":  
                    $output .= sprintf("\\u%04x", $chrNum);  
                  break;  
                  default:  
                    $output .= $str[$i];  
                  break;  
                 }  
               }  
               return $output;  
             }  
             ?>

  ```
  
Here is how to use the `jsEscape` function in PHP:  
```js 
<script>x = '<?php echo jsEscape($_GET['x'])?>';</script>
```

Alternatively, you could use a template engine.