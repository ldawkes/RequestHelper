Provides Laravel-like request validation without all the overhead.

> **Note:** More rules are still yet to be added

## Basic Usage

```php
	// Ruleset with key matching request parameter and value matching rules
	$rules = [
    	"name" 		=> "required|string",
        "age" 		=> "numeric",
        "consent" 	=> "required_without:age"
    ];
    
    // Aliases for request parameters with special characters
    $aliases = [
    	"name" => "Full Name"
    ];
    
    // Will either be true for success, or an array of error messages
    $result = RequestHelper::validatePost($rules, $aliases);
```

## Available Methods

| Method           | Purpose
| ---              | ---
| **validateGet**  | Validates GET parameters
| **validatePost** | Validates POST parameters

## Available Rules

| Name                             | Behaviour                                                | Example
| ---                              | ---	                                                  | ---
| **required**                     | *A required parameter*                                   | ```"name" => "required```
| **required_without**:*parameter* | *Parameter is only required when another is missing*     | ```"age" => "required_without:consent"```
| **null**                         | *Checks that parameter is null*                          | ```"human_check_hidden" => "null"```
| **string**                       | *Checks parameter only contains alphanumeric characters* | ```"message" => "string"```
| **email**                        | *Checks parameter is a valid email*                      | ```"email" => "required\|email"```
| **decimal**                      | *Checks parameter is a valid decimal number*             | ```"result" => "decimal"```
| **phone**                        | *Checks parameter is a valid phone number*               | ```"phone_no" => "phone"```
| **array**                        | *Checks parameter is a valid array*                      | ```"choices" => "required\|array"```
| **same_as**:*parameter*          | *Checks that parameter is the same as another*           | ```"password_check" => "password"```