# DBPractice

Contains Queries from Stanford SQL excercises

1) Movie Rating

2) Social Network


### Basic authentication
[ExternalTRTaxService_TaxServiceExport](mockbox-dev/src/main/resources/jsondb/ExternalTRTaxService_TaxServiceExport) has basic authentication enabled and can be used to accept recieve a fake SOAP response.

How to use it?

It uses mockTR resource defined in custom_handler.js. An example for a simple get request is given below. It can be used to get a SOAP like response by setting Content-Type and Accept headers to application/xml. 
```
$ curl -X GET -H "Authorization: Basic c2FwYXJpYmFkZXY6RmJqeGo5RQ==" -H "accept: application/xml" 
  "http://localhost:8003/mockbox/v1/rest/ExternalTRTaxService/TaxServiceExport/api/mockTR"
<ScriptObjectMirror>
  <SOAP-ENV:Envelope></SOAP-ENV:Envelope>
  <SOAP-ENV:Header></SOAP-ENV:Header>
  <SOAP-ENV:Body></SOAP-ENV:Body>
</ScriptObjectMirror>
```

It also supports POST. To see the soap response with POST, send a simple xml data in the body

```
$ curl -X POST -H "Authorization: Basic c2FwYXJpYmFkZXY6RmJqeGo5RQ==" -H "accept: application/xml" -H "Content-Type: application/xml" -d "<id>1</id>" https://dev2-mu.mo.sap.corp/mockbox/mockbox/v1/rest/ExternalTRTaxService/TaxServiceExport/api/mockTR

<ScriptObjectMirror>
  <SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
    <SOAP-ENV:Header></SOAP-ENV:Header>
    <SOAP-ENV:Body>
      <ns2:TaxServiceExportReply xmlns:ns2="urn:Ariba:Buyer:vsap">
        <ns2:Requisition_TaxServiceAPIResponse_Item>
          <ns2:item>
            <ns2:ExternalTaxResponseStatus>
              <ns2:Success>true</ns2:Success>
            </ns2:ExternalTaxResponseStatus>
            <ns2:LineItems>
              <ns2:item>
                <ns2:ExternalTaxItem>
                  <ns2:item>
                    <ns2:AbatementPercent>100.0</ns2:AbatementPercent>
                    <ns2:Category>S</ns2:Category>
                    <ns2:Description>GST</ns2:Description>
                    <ns2:ExternalTaxType>
                      <ns2:UniqueName>GST</ns2:UniqueName>
                    </ns2:ExternalTaxType>
                    <ns2:FormulaString>GCBG1: Standard input GST in Ship To location.|10000|P</ns2:FormulaString>
                    <ns2:IsDeductible>false</ns2:IsDeductible>
                    <ns2:Percent>5.0</ns2:Percent>
                    <ns2:TaxAmount>
                      <ns2:Amount>49.4</ns2:Amount>
                      <ns2:Currency>
                        <ns2UniqueName>CAD</ns2UniqueName>
                      </ns2:Currency>
                    </ns2:TaxAmount>
                    <ns2:TaxableAmount>
                      <ns2:Amount>987.99</ns2:Amount>
                      <ns2:Currency>
                        <ns2:UniqueName>CAD</ns2:UniqueName>
                      </ns2:Currency>
                    </ns2:TaxableAmount>
                  </ns2:item>
                </ns2:ExternalTaxItem>
                <ns2:NumberInCollection>1</ns2:NumberInCollection>
                <ns2:TaxCode>
                  <ns2:Country>
                    <ns2:UniqueName>CA</ns2:UniqueName>
                  </ns2:Country>
                  <ns2:UniqueName>V1</ns2:UniqueName>
                </ns2:TaxCode>
              </ns2:item>
            </ns2:LineItems>
            <ns2:UniqueName>DOC1</ns2:UniqueName>
          </ns2:item>
        </ns2:Requisition_TaxServiceAPIResponse_Item>
      </ns2:TaxServiceExportReply xmlns:ns2="urn:Ariba:Buyer:vsap">
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
</ScriptObjectMirror>
```
