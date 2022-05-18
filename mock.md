# Mock function description

Front-end development often relies on back-end data interfaces. Before the back-end interfaces are ready, the front-end is usually difficult to start. The Mock function is used to solve this problem. With the Mock tool, the front-end and back-end can be developed simultaneously. Before the back-end interface comes out, the front-end can use the Mock function to create a fake data interface for development and debugging.

## Function description

The Mock function can automatically generate mock data according to `the interface/data structure definition`, `Mock rule configuration`, `Mock expectation configuration`. And users can flexibly construct interface data of various structures according to their needs.

Usually, Apifox can generate very user-friendly mock data with `zero configuration`:

1. Apifox automatically generates mock rules based on the data structure and data type in the interface definition.
2. Apifox has a built-in [smart mock](https://www.apifox.cn/help/app/mock/intelligent-mock/) function, which intelligently optimizes the automatically generated mock rules according to the field name and field data type. For example: a `string` type field whose name contains the string `image` will automatically mock out an image address URL; a `string` type field containing the string `time` will automatically mock a time string; a `string` type field containing the string `city`, which automatically mocks out a city name.
3. According to built-in rules (which can be turned off), Apifox can automatically identify fields such as pictures, avatars, usernames, mobile phone numbers, URLs, dates, times, timestamps, emails, provinces, cities, addresses, IPs, etc., so that Mock is very user-friendly. 
4. In addition to the built-in mock rules, users can also customize the rule base to meet various personalized needs. Supports custom mock rules using `regular expressions` and `wildcards` to match field names.

The data effect of Apifox `zero configuration` Mock:

![Apifox Mock 数据结果对比同类工具](https://cdn.apifox.cn/mirror-www/help/assets/img/mock-result-apifox.9cc55178.jpg)

## Mock request URL

Mock URL supports two modes:
1. Interface path mode: `http://127.0.0.1:4523/mock/{project ID}{interface path}`
2. Interface ID Mode: `http://127.0.0.1:4523/mock2/{Project ID}/{Interface ID}`

The request `method` is consistent with the `method` defined by the interface.

If your project ID is `18600`, the interface ID of the Mock is `89343`, the path is `/store/pets`, and requests the `method` as `POST`. The actual Mock URL is:

```
POST http://127.0.0.1:4523/mock/18600/store/pets
or
POST http://127.0.0.1:4523/mock2/18600/89343
```

By default, after defining `the interface/data structure`, you can access the data interface automatically mocked through the above URL without any additional configuration.

> 1. The mock service is started locally, so the ip address in the URL is `127.0.0.1`. If other devices need to access mock data, just change `127.0.0.1` to the local intranet ip. If it still cannot be accessed, please check whether the firewall etc. restrict the port `4523` used by mock.
> 2. If there are multiple interfaces with the same `method + path` in a project, only **the interface ID mode** can be used, and **the interface path mode** cannot be used, otherwise a path conflict will occur.
> 3. If the interface path does not start with `/`, only **the interface ID mode** can be used, and **the interface path mode** cannot be used.
> 4. Opening Apifox will start the mock service by default, no additional action is required.
> 5. The `pre-URL` of the Mock service is fixed and cannot be modified. Modifying the `pre-URL` in an environment called `Mock Server` does not change the actual `pre-URL` of the Mock service.

### Get interface mock URL

Open the `interface details - view` the Mock module in , you can get the mock URLs of the corresponding interface

![Apifox 获取接口 mock URL](https://cdn.apifox.cn/mirror-www/help/assets/img/mock-mock-urls.8b27796e.jpg)

## Custom Mock Rules

Apifox supports very flexible mock rule definitions to meet various business needs.

### 1. Data structures define mock rules

When defining the data structure, you can manually set the mock rules, support the [Mock.js](http://mockjs.com/) `data placeholder definition` method to write the Mock rules, [check the Mock.js syntax](http://mockjs.com/examples.html#DPD)

![Apifox 数据结构定义 Mock 规则](https://cdn.apifox.cn/mirror-www/help/assets/img/mock-setting-schema.930aa410.jpg)

### 2. Data Field Advanced Settings

The maximum value, minimum value, enumeration value, Partten, format set in the advanced settings of the data field, Also used as a Mock rule:

![Apifox 数据结构高级设置 Mock 规则](https://cdn.apifox.cn/mirror-www/help/assets/img/mock-setting-schema-advance.315b666f.jpg)

### 3. Advanced Mock

Advanced mock is the most flexible mock method, which can implement flexible custom data structure (not limited by interface data structure), and can return different data according to different request parameter values. [View Advanced Mock Documentation](https://www.apifox.cn/help/app/mock/mock-custom-scripts/)

### 4. Intelligent Mock

When mock rules are not configured for the fields in the returned Response (or data model) of the interface design, the system will automatically use smart mock rules to generate data, so that very user-friendly data can be mocked with `zero configuration` when used. [View Smart Mock documentation](https://www.apifox.cn/help/app/mock/intelligent-mock/)


## Mock rule priority

When the data field is automatically mocked, the Mock rules that are actually executed are in the following priority order:

1. In interface details, `expectations` set in `advanced mocks` (matched according to interface parameters).
2. `Mock` rules set in the fields of the data structure.
3. The `maximum value`, `minimum value`, `enumeration value`, `Parten`, and `format` set in the `advanced` field settings of the data structure.
4. `Project Settings - Custom rules for smart Mock Settings`.
5. `Project Settings - Built-in rules for smart Mock settings`.
6. The `data type` of the field in the data structure.

## Other

By default, the system will mock the data structure of the first Response in the interface definition. If you need to mock other Responses, you can get the mock URLs of other Responses in the Mock module of the interface details - view page.



