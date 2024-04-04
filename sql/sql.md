---
title: SQL Common Errors
format:
  html:
    toc: true
    toc-depth: 5
    toc-location: right
    code-fold: false
    theme:
      - cosmo
      - cerulean
    callout-icon: false
jupyter:
  jupytext:
    text_representation:
      extension: .qmd
      format_name: quarto
      format_version: "1.0"
      jupytext_version: 1.16.1
  kernelspec:
    display_name: Python 3 (ipykernel)
    language: python
    name: python3
---

## `NameError: name ‘...’ is not defined`

This error usually occurs when you have a syntax error or incorrect reference somewhere in your `SQL` code, preventing the query from being run.

There is usually a less visible error message outputted right after the cell where the syntax error occurred. The output starts with `Running query` and reading it should be helpful in in identifying the error.

#### **Some scenarios and fixes**

**1. Incorrect Alias Usage**

- **Issue:** Referring to a column or table using its original name instead of the alias assigned with the `AS` keyword.
- **Solution:** Always use the alias, if you have assigned one, when referencing a column or table. For example, if you set `SELECT column AS col FROM table`, use `col` in your subsequent references.

**2. Ambiguous Column Reference in Joins**

- **Issue:** Referring to a column that exists in both tables being joined, without specifying which table's column to use.
- **Solution:** Specify the table from which to select the column from. Use the format`tableName.columnName` to clear up the ambiguity. For example, if joining `tableA` and `tableB`, both containing `column`, specify `tableA.column` or `tableB.column`.

## Filtering with multiple conditions

When you are using more than one condition in filtering clauses such as `WHERE` or `HAVING`, it is important to keep in mind that the ordering of `OR`s and `AND`s will affect your SQL output.

In `SQL`, the operator precedence typically evaluates `AND` operations before `OR` operations, and so incorrectly ordered conditions can lead to unexpected results. To ensure your conditions are evaluated in the intended order, use parentheses to group them explicitly.

Consider the following query condition:

`WHERE A > 500 AND B > 200 OR C < 50`

By default is it is evaluated as the following since `AND` has a higher precedence than `OR`:

`WHERE (A > 500 AND B > 200) OR C < 50`

We might instead have wanted to evaluate it is as the following and so we have to use parentheses to specify the order of operations:

`WHERE A > 500 AND (B > 200 OR C < 50)`

## Incorrect data types with `CAST`

It is important to use only the supported data types when casting, otherwise the query will result in an error. SQL supports casting to and from the following data types:

- **Integer Types**: `bigint`, `int`, `smallint`, `tinyint`
- **Boolean Type**: `bit`
- **Decimal Types**: `decimal`, `numeric`, `money`, `smallmoney`
- **Floating Point Types**: `float`, `real`
- **Date and Time Types**: `datetime`, `smalldatetime`
- **Character Strings**: `char`, `varchar`, `text`
- **Unicode Character Strings**: `nchar`, `nvarchar`, `ntext`
- **Binary Strings**: `binary`, `varbinary`, `image`

For example, doing `CAST(num AS integer)` will error since `int` is a supported data type, but `integer` is not.

## Frame not returned when using (...) in filtering

In `SQL`, tuples are a sequence of values grouped together by parenthesis. They are meant for use with the `IN` keyword when filtering data based on set membership. You need to be careful when using tuples with other filtering keywords such as `LIKE`.

#### **Incorrect usage:**

1.  `WHERE item LIKE ('%orange%' OR '%strawberry%')`
2.  `WHERE item IN ('fruit', 'vegetable')`

#### **Correct usage:**

1. `WHERE (item LIKE '%orange%' OR item LIKE '%strawberry%')`
2. `WHERE item IN ('fruit', 'vegetable')`
