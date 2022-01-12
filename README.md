# TestRunner

Test Driven Development Runner.  
Write input, expected output, and how to execute.

## File Structure

A directory should be dedicated for each test app you want to run. The directory should be structured as follows:

```
/tests_for_testrunner
├── config.json
├── /test1
│   ├── input.json
│   └── output.json
├── /test2
│   ├── input.json
│   └── output.json
```

## Config

Example json config. Allowed properties are:

- `endpoint` - The endpoint to hit.
- `method` - The http method to use.
- `headers` - A map of headers by key value pairs.
- `custom` - A list of configuration values to be used for specific test cases.
  These will be run in the order defined by `dependencies`, if defined.
  These will be run at the beginning of the test suite in order, and will override the config settings at the top level of this file if defined in the `custom` object. The `testcase` property is required for each of these objects.

```json
{
  "endpoint": "https://example.com",
  "method": "POST",
  "headers": {
    "client_id": "asdfasdfa",
    "client_secret": "lkjhlkjhlkjhlkjh"
  },
  "custom": [
    {
      "testcase": "test2",
      "endpoint": "https://example.com/es_o_houlihan",
      "method": "PATCH",
      "headers": {
        "Authorization": "Bearer zxcvzxcvzxcvzxcvzxcvzxcvzxcvzxcv"
      },
      "dependencies": ["test1"]
    }
  ]
}
```
