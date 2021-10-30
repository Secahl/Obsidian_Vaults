## Providing an encryption oracle
  
Dangerous scenarios can occur when user-controllable input is encrypted and the resulting ciphertext is then made available to the user in some way.  
  
>This kind of input is sometimes known as an "**encryption oracle**".  
_An attacker can use this input to encrypt arbitrary data using the correct algorithm and asymmetric key._  

This becomes dangerous when there are other user-controllable inputs in the application that expect data encrypted with the same algorithm.  
In this case, an attacker could potentially use the encryption oracle to generate valid, encrypted input and then pass it into other sensitive functions.  
>_This issue can be compounded if there is another user-controllable input on the site that provides the_ _reverse function_.
  
This would enable the attacker to decrypt other data to identify the expected structure.  
This saves them some of the work involved in creating their malicious data but is not necessarily required to craft a successful exploit.  
  
`The severity of an encryption oracle depends on what functionality also uses the same algorithm as the oracle.`  
  
  
>LAB [Authentication bypass via encryption oracle](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-authentication-bypass-via-encryption-oracle)