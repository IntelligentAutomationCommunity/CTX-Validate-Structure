# CTX-Validate-Structure
This project contains subtasks that can be used to validate and sanitise fields in a structure according to a provided specification


## Inputs
The subtask accepts the following inputs:
- **i_structure**: the structure to be provided
- **i_specification**: a list of validations to be applied to the structure; see below for more information
- **i_structure-label**: an optional label for the structure to be used in error messages

## Outputs
The subtask provides the following outputs:
- **o_sanitised_output**: a structure representing the result of applying the validation specification to the input structure
- **o_Errors**: a list of error messages generated during the validation process

## Validation
The input structure is copied to the output structure and it is validated and sanitised according to the elements of the **i_specification** input list.

The **i_specification** input list provides details on the validations to apply. Each element of the list is a validation structure, with the following fields:
Field Name | Description | Type | M/O |
-----------|-------------|------|-----|
**NAME**|The name of the field in the **i_structure** input structure to which this validation applies|text|M
**MANDATORY**|An indication of whether the field should exist in the input structure|true or false|M
**TYPE**|The type of the field; see below for details on supported types|text|M
**DEFAULT**|A value to use if the field is not present in the input structure; a field will be added to the **o_sanitised_output** output structure with this value|text or integer|O
**PATTERN**|A regular expression used to validate fields of type "text"|text|O
**VALUES**|A list of valid string values used to validate fields of type "text"|text|O
**INCL_MIN**|The minimum value used to validate fields of type "integer"|integer|O
**INCL_MAX**|The maximum value used to validate fields of type "integer"|integer|O
**VALIDATION**|A list used to validate sub-structures or sub-lists in the input structure. Each element of this list must conform to a validation structure similar this **i_specification** input format. This validation may include validation of sub-sub-structures or sub-sub-lists, and so on|list|O

### Types
The following types are supported by the subtask; you may add additional types as required
- **text** - a string of characters; fields of this type are sanitised by removing single- and double-quote characters
- **integer** - a number
- **structure** - a structure; fields in this structure will be validated according to the **VALIDATION** field in the validation structure
- **structure-list** - a list of structures; each structure in the list will be validated according to the **VALIDATION** field in the validation structure

# Installation Instructions
Download the Studio Package file and Import it into your Cortex Environment.
Don't forget to apply rights using the Studio Authorization module.

:thumbsup: Enjoy! :wink:
