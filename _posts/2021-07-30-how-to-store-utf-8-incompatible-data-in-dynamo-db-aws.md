---
layout: post title:  "How to store UTF-8 incompatible data in DynamoDB?"
date:   2021-07-30 25:50:15 +0200 categories: [aws]
---

When storing data as strings in DynamoDB
you [must be compatible with UTF-8](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.NamingRulesDataTypes.html#HowItWorks.DataTypes.String)
. Sometimes however you may need to store data in DynamoDB which isn't compliant with UTF-8. For example if you want to
use DynamoDB as a Cache for Favicon data.

To solve this issue you can convert the data of your string to hexadecimal before sending it to AWS. For example in PHP:
```php
$nonUTF8Data = "some non utf-8 data";
$hexNonUTF8Data = bin2hex($nonUTF8Data);
// Write $hexNonUTF8Data to DynamoDB
```

Receiving hex data from DynamoDB
```php
// Receive hexadecimal DynamoDB data $hexNonUTF8Data
$nonUTF8Data = hex2bin($hexNonUTF8Data);
```

See the documentation for [bin2hex](https://www.php.net/manual/en/function.bin2hex.php) and [hex2bin](https://www.php.net/manual/en/function.hex2bin.php)
