---
title: Example of an Option Type Record
---
Option types can easily represent some common input types, including text, number, radio, checkbox, and dropdown/multiple choice.

###JSON Parameters

[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Description",
    "0-0": "name",
    "0-1": "The name of the option type for handy reference",
    "1-0": "description",
    "1-1": "Short description of the option type (the CLI actually shows this when pressing `?` for help)",
    "2-0": "fieldName",
    "3-0": "fieldLabel",
    "4-0": "fieldContext",
    "5-0": "placeHolder",
    "6-0": "helpBlock",
    "7-0": "defaultValue",
    "2-1": "The property key for when posting this option type to a JSON POST request",
    "3-1": "User friendly label for prompting a user for input",
    "4-1": "Some properties need nested i.e. in a `config: {}` block. This is a `.` separated context of where the property should be constructed",
    "5-1": "Any placeholder text when nothing is yet entered",
    "6-1": "Short help text describing the option",
    "7-1": "The default value if no user entry is specified. This value should be passed to the desired JSON Map if nothing else is entered",
    "8-0": "optionSource",
    "9-0": "type",
    "10-0": "required",
    "11-0": "editable",
    "12-0": "displayOrder",
    "13-0": "config",
    "8-1": "Option source references an API endpoint for receiving a JSON list of available options for this field.",
    "9-1": "The type of input. I.e. text, select, radio,checkbox, etc.",
    "10-1": "Is this field entry required for the request",
    "11-1": "Used primarily on tasks and workflows. Basically wether or not the field can be overridden optionally when the object is run",
    "12-1": "The order with which the fields should be prompted. This is rather important when using optionSource in some scenarios for determining available values.",
    "13-1": "Any special configuration options pertaining to specific input types, like a radio button."
  },
  "cols": 2,
  "rows": 14
}
[/block]
###Example
[block:code]
{
  "codes": [
    {
      "code": "{\n    \"optionTypes\": [\n                {\n                    \"name\": \"subnet\",\n                    \"description\": null,\n                    \"fieldName\": \"subnetId\",\n                    \"fieldLabel\": \"Subnet\",\n                    \"fieldContext\": \"config\",\n                    \"fieldAddOn\": null,\n                    \"placeHolder\": null,\n                    \"helpBlock\": \"\",\n                    \"defaultValue\": null,\n                    \"optionSource\": \"amazonSubnet\",\n                    \"type\": \"select\",\n                    \"advanced\": false,\n                    \"required\": true,\n                    \"editable\": false,\n                    \"config\": [],\n                    \"displayOrder\": 100\n                },\n                {\n                    \"name\": \"security group\",\n                    \"description\": null,\n                    \"fieldName\": \"securityId\",\n                    \"fieldLabel\": \"Security Group\",\n                    \"fieldContext\": \"config\",\n                    \"fieldAddOn\": null,\n                    \"placeHolder\": null,\n                    \"helpBlock\": \"\",\n                    \"defaultValue\": null,\n                    \"optionSource\": \"amazonSecurityGroup\",\n                    \"type\": \"select\",\n                    \"advanced\": false,\n                    \"required\": true,\n                    \"editable\": false,\n                    \"config\": [],\n                    \"displayOrder\": 101\n                },\n                {\n                    \"name\": \"public key\",\n                    \"description\": null,\n                    \"fieldName\": \"publicKeyId\",\n                    \"fieldLabel\": \"Public Key\",\n                    \"fieldContext\": \"config\",\n                    \"fieldAddOn\": null,\n                    \"placeHolder\": null,\n                    \"helpBlock\": \"\",\n                    \"defaultValue\": null,\n                    \"optionSource\": \"keyPairs\",\n                    \"type\": \"select\",\n                    \"advanced\": false,\n                    \"required\": false,\n                    \"editable\": false,\n                    \"config\": [],\n                    \"displayOrder\": 9\n                }\n            ]\n}",
      "language": "json"
    }
  ]
}
[/block]
