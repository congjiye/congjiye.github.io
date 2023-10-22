---
title: JSON schema入门指北
date: 2023-10-22 22:13:52
tags:
  - JSON
category: 工具
---

## 什么是 JSON schema

JSON schema 是对 JSON 文件结构进行校验的一种工具，可以理解为模式或者规则。

通过利用 JSON schema 可以帮助我们识别 JSON 文件中的错误信息。

<!-- more -->

## JSON 数据类型

| 类型      | 描述                             |
|---------|--------------------------------|
| string  | 字符串型，双引号包裹的 Unicode 字符和反斜杠转义字符 |
| number  | 数字型，包括整型(int)和浮点数型(float)      |
| boolean | 布尔型，true 或 false               | 
| object  | 对象型，无序的键:值对集合                  |
| array   | 数组型，有序的值序列                     |
| null    | 空型                             |

## JSON 关键字

### string

| 关键字       | 描述   | schema 有效值      | json 数据验证         |
|-----------|------|-----------------|-------------------|
| maxLength | 最大长度 | 大于等于 0 的整数      | 字符串的长度必须小于等于该值    |
| minLength | 最小长度 | 大于等于 0 的整数      | 字符串的长度必须大于等于该值    | 
| pattern   | 模式   | 字符串，必须是有效的正则表达式 | 当字符串符合正则表达式时，通过验证 |

### number

| 关键字              | 描述    | Schema 有效值                                              | json 数据验证                |
|------------------|-------|---------------------------------------------------------|--------------------------|
| multipleOf       | 整数倍   | 大于 0 的 JSON 数                                           | 当 JSON 实例的值是其整数倍的时候，通过验证 | 
| maximum          | 最大值   | 一个 JSON 数当 JSON 实例的值小于等于 maximum 的时候，通过验证               |
| exclusiveMaximum | 包含最大值 | 布尔值，必须与 maximum 一起使用当其为 true 的时候，JSON 实例不能等于 maximum 的值 |
| minimum          | 最小值   | 一个 JSON 数当 JSON 实例的值大于等于 minimum 的时候，通过验证               |
| exclusiveMinimum | 包含最小值 | 布尔值，必须与 minimum 一起使用当其为 true 的时候，JSON 实例不能等于 minimum 的值 |

### array

| 关键字             | 描述    | Schema 有效值                              | json 数据验证                                                                                                                                           |
|-----------------|-------|-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| items           | 定义元素  | 必须是 Schema 实例对象或者 Schema 实例对象的数组        | 用于定义 array 中的元素类型                                                                                                                                   |
| additionalItems | 额外项校验 | 布尔值或 Schema 实例对象                        | 当 items 为 Schema 实例的数组，additionalItems 为 false 时，json 数据长度必须小于等于 items 长度，如果 additionalItems 是 Schema 实例，则 items 关键字指定的 Schema实例数组没有匹配到的其他元素都要符合该实例 |
| maxItems        | 长度限制  | 大于等于 0 的整数array 实例的长度必须小于等于 maxItems 的值 |
| minItems        | 长度限制  | 大于等于 0 的整数array 实例的长度必须大于等于 minItems 的值 |
| uniqueItems     | 唯一值   | 布尔值，默认值 false                           | 当uniqueItems 为 true 的时候，array 实例不能有重复值。                                                                                                             |

### object

| 关键字                  | 描述     | Schema 有效值                                      | json 数据验证                                                                                     |
|----------------------|--------|-------------------------------------------------|-----------------------------------------------------------------------------------------------|
| properties           | 属性     | 属性的值必须都是有效的 Schema 实例对象                         | 用于定义属性列表                                                                                      |
| maxProperties        | 最大属性个数 | 大于等于0 的整数object 实例的属性个数必须小于等于 maxProperties 的值  |
| minProperties        | 最小属性个数 | 大于等于 0 的整数object 实例的属性个数必须大于等于 minProperties 的值 |
| required             | 必须属性   | 字符串数组，至少必须有一个元素，数组内不能有重复值                       | object 实例必须有所有 required 定义的属性                                                                 |
| patternProperties    | 按属性名校验 | 必须是有效的 Scheme 实例对象                              | Scheme 实例的每一个属性的键都是一个正则表达式，值都是一个 Schema 实例。 指定符合正则表达式的属性的校验规则                                 |
| additionalProperties | 额外属性校验 | Scheme 实例对象或布尔值                                 | 为 false 时不允许拥有除了 properties 和 patternProperties 匹配到的属性外的属性，如果为 Scheme 实例，则没有匹配到的属性要符合该 Scheme |

### 通用关键字

| 关键字   | 描述   | Schema 有效值                                | json 数据验证                                                                 |
|-------|------|-------------------------------------------|---------------------------------------------------------------------------|
| enum  | 数据枚举 | 必须是数组，而且数组里面的元素至少必须有一个而且不能有重复值            | 当 json 实例的值存在于 enum 列表中时，通过验证                                             |
| type  | 定义类型 | 可以是字符串或者字符串数组，取值必须在 JSON 基本类型范围内          | 校验 JSON 实例的类型是否符合定义                                                       | 
| allOf | 数据验证 | 必须是 Schema 实例对象数组，而且数组里面的元素至少必须有一个而且不能有重复 | JSON 实例满足其中所有的 Schema 时，通过验证                                              |
| anyOf | 数据验证 | 同 allOf                                   | JSON 实例满足其中某一个 Schema 时，通过验证                                              | 
| oneOf | 数据验证 | 同 allOf                                   | JSON 实例刚好只满足其中某一个 Schema 时，通过验证                                           |
| not   | 数据验证 | 必须是个有效的 Schema 实例对象                       | 如果不满足 JSON Schema的定义，则通过验证const数据验证JSON 基本类型如果 JSON 实例的值和该关键字指定的值相同，则通过校验 |

## Schema 示例

```json
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "$id": "https://example.com/schemas/person",
  "title": "Schema Example",
  "description": "JSON schema example",
  "type": "object",
  "required": [
    "name"
  ],
  "definitions": {
    "name": {
      "type": "string",
      "minLength": 1,
      "maxLength": 10
    }
  },
  "properties": {
    "name": {
      "type": "string",
      "minLength": 1,
      "maxLength": 10
    },
    "age": {
      "type": "number",
      "minimum": 18,
      "exclusiveMinimum": true,
      "maximum": 65,
      "exclusiveMaximum": true
    },
    "phone": {
      "type": "string",
      "pattern": "^1\\d{10}$"
    },
    "parents": {
      "type": "array",
      "items": [
        {
          "$ref": "#/definitions/name"
        }
      ],
      "minItems": 1,
      "maxItems": 2,
      "uniqueItems": true
    },
    "address": {
      "type": "object",
      "properties": {
        "city": {
          "type": "string",
          "enum": [
            "guangzhou",
            "beijing"
          ]
        }
      }
    }
  }
}
```

