schemas used in signalsd testing


 ⚠ take care if editing existing schemas as you may break tests that prevent the application being deployed. if in doubt, create a new one.

# simple.json 
a simple schema to test basic signal handling.  

This schema can be used when testing the signal type schema registration handler with a real github schema.

sample signal json payload:
```json
{
    "test": "Hello, world!"
}
```