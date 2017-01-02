+++
title = "DomainTransfer"
toc = true
+++

Sends the Transfer command to the registrar for the domain

Connects to the registrar and attempts to start the transfer process.

### Request Parameters

| Parameter | Type | Description | Required |
| --------- | ---- | ----------- | -------- |
| action | string | "DomainTransfer" | Required |
| domainid | int | The id of the domain to obtain the whois information for *recommended* | Optional |
| domain | string | The domain name to be registered. This or $domainid is required | Optional |
| eppcode | int | Provide a new EPP Code for the Transfer Request | Optional |

### Response Parameters

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| result | string | The result of the operation: success or error |


### Example Request (CURL)

```
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'https://www.example.com/includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS,
    http_build_query(
        array(
            'action' => 'DomainTransfer',
            'username' => 'ADMIN_USERNAME',
            'password' => 'ADMIN_PASSWORD',
            'domainid' => '1',
            'responsetype' => 'json',
        )
    )
);
$response = curl_exec($ch);
curl_close($ch);
```


### Example Request (Local API)

```
$command = 'DomainTransfer';
$postData = array(
    'domainid' => '1',
);
$adminUsername = 'ADMIN_USERNAME';

$results = localAPI($command, $postData, $adminUsername);
print_r($results);
```


### Example Response JSON

```
{
    "result": "success"
}
```


### Error Responses

Possible error condition responses include:

* Domain Not Found
* Registrar Error Message


### Version History

| Version | Changelog |
| ------- | --------- |
| 1.0 | Initial Version |