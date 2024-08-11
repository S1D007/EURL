# EURL: A Comprehensive HTTP Client Tool

## Abstract

EURL is a modern HTTP client designed to offer robust functionality for making HTTP requests. It supports a wide range of HTTP methods, payload types, and headers, and includes advanced features like logging, observability, and request pipelining. EURL is designed to cater to various programming languages and focuses solely on HTTP and HTTPS protocols.

## 1. Introduction

EURL is an alternative to cURL, aiming to provide a versatile and user-friendly tool for interacting with web services. It supports essential HTTP methods, flexible payload handling, extensive header customization, and advanced features for logging and request management.

## 2. Core Features

### 2.1 HTTP Methods Support

EURL supports the following HTTP methods:

- **GET**: Retrieve data from a specified resource.
- **POST**: Submit data to be processed to a specified resource.
- **PUT**: Update a specified resource with new data.
- **PATCH**: Apply partial modifications to a specified resource.
- **DELETE**: Remove a specified resource.

### 2.2 Payload Handling

EURL can handle various types of payloads, including:

- **JSON**: Commonly used format for API requests.
- **Form Data**: For submitting form submissions.
- **XML**: Used in some legacy systems.
- **Binary Data**: For file uploads and other binary content.

Payloads can be sourced from:

- **Inline Data**: Directly specified within the request.
- **Files**: Read from local file systems or remote sources.
- **Streams**: Data streamed from other processes or sources.

### 2.3 Header Support

EURL allows extensive header customization, including:

- **Custom Headers**: Define any header required by the server.
- **Authorization**: Support for various authorization schemes (e.g., Bearer tokens, Basic Auth).
- **Content-Type**: Specify the media type of the request body.
- **Accept**: Specify the media type that the client is willing to receive.

### 2.4 Logging and Observability

EURL provides comprehensive logging and observability features:

- **File System Level Logging**: Logs request and response details to the local file system.
- **Custom Log Levels**: Configurable log levels (e.g., INFO, DEBUG, ERROR).
- **Metrics Collection**: Track request performance and error rates.
- **Real-Time Monitoring**: Option for real-time log streaming and monitoring.

### 2.5 Pipeline Maker

EURL includes a pipeline feature that allows users to chain multiple requests:

- **Request Chaining**: Pipe the output of one request as the input to another.
- **Data Transformation**: Process and transform data between requests.
- **Error Handling**: Configure error handling and fallback strategies.

### 2.6 Package Support

EURL is available as a package for various programming languages:

- **Python**: Installable via pip. (INP)
- **JavaScript/Node.js**: Installable via npm.
- **Java**: Available as a Maven dependency. (INP)
- **Ruby**: Installable via gem. (INP)
- **C#**: Available as a NuGet package. (INP)

### 2.7 Protocol Support

EURL exclusively supports HTTP and HTTPS protocols:

- **HTTP**: For unencrypted requests.
- **HTTPS**: For encrypted requests, ensuring secure data transmission.

## 3. Installation and Setup

### 3.1 Installation

To install EURL, follow the respective instructions for your programming language:

- **Python**: `pip install eurl` (INP)
- **JavaScript/Node.js**: `npm install eurl`
- **Java**: Add dependency in `pom.xml` (INP)
- **Ruby**: `gem install eurl` (INP)
- **C#**: Install via NuGet Package Manager (INP)

### 3.2 Configuration

EURL provides a configuration file for setting up default values:

- **config.yml**: Specify default headers, logging settings, and other preferences.

## 4. Usage Examples

### 4.1 BASICS with Language Support (JS/TS)

```javascript
const Eurl = require("eurl");
const e = Eurl({
  logging: "verbose",
  // remote
  logFile: ["log.el", "https://s3.aws.com/.../..."],
  catch: (error) =>
    EURL.ERROR({
      timestamp: true,
      status: true,
      hostname: true,
      message: "simplified",
    }),
    headers: [{
        Authorization: `Bearer $1` // $natual_number represents data you want to replace with, if allowed it will persist
    },{},{}] // add default headers
});
const data = await eurl.post("https://api.example.com/resource", {
  data: { key: "value" },
  headers: { Authorization: "Bearer token" },
}, [{Authorization:["$1", "$response.token"], persist: true}]); // will result in "Bearer abc1234qqwqsas", if it is persisted true it will be used in every request
// pipe to different request
const data2 = eurl.get((data) => `https://abc.com/users/${data.name}`);
const { response } = data.pipe(data2);
```

### 4.3 Request Pipelining (.eurl file)

```ruby
pipeline = eurl.pipeline do
  request 'https://api.example.com/resource1'
  transform { |data| process_data(data) }
  request 'https://api.example.com/resource2', data: transformed_data
end

pipeline.execute
```

## 5. Advanced Features

### 5.1 Logging Configuration

Configure logging in `config.yml`:

```yaml
logging:
  level: DEBUG
  path: /var/log/log.el
  methods:
  - PUT
  - POST
  - DELETE
  ... more comming
```

## 6. Conclusion

EURL is a powerful and flexible HTTP client that provides comprehensive support for various HTTP methods, payload types, and advanced features. Its focus on ease of use, extensive logging, and support for multiple programming languages makes it a valuable tool for developers working with web services.