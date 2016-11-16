# DBPractice

Contains Queries from Stanford SQL excercises

1) Movie Rating

2) Social Network


### Basic authentication
[ExternalTRTaxService_TaxServiceExport](mockbox-dev/src/main/resources/jsondb/ExternalTRTaxService_TaxServiceExport). Attributes defined for authorization are the only essential attributes.

How to use it?
With no basic auth header
```
$ curl -X GET -H "Content-Type: application/x-www-form-urlencoded" \
  -H "Accept: application/json" \
  "http://localhost:8003/mockbox/v1/rest/basicauthexample/v0.2/api/users"
{
  "error" : "invalid_data",
  "description" : "Invalid data provided."
}
```
