# SQL Injection

A SQL Injection (SQLI) is an attack where one injects unwanted queries into a
database where they are executed. This attack vector arises when user input is
not properly sanitized. For example, assume we have a website with a search
field which relies on the following query:

```sql
SELECT name, description FROM products
WHERE name=search_query;
```

If a malicious user enters `x'; DROP TABLE products;` this would turn into

```sql
SELECT name, description FROM products
WHERE name='x';
DROP TABLE products;
```

which is bad mkay.

## Detecting SQLI

There are several ways of detecting SQLI vulnerabilities. If when entering `'`
one gets a server error there might be a vulnerability.

Note that this might change depending on what database language is used.

## Second Order Injection

A second order injection is when e.g. a username with unescaped characters is
stored and the SQL injection attack runs when e.g. the user changes password.

## Login SQLI

SQLI attacks can be used on login forms. Typically when logging in, a SQL query
of the form

```sql
SELECT * FROM users
WHERE username=entered_username
AND password=entered_password;
```

A SQLI attack on a login from could be using username and password of
`' OR ''= '`. If input is not sanitized this would generate the following query

```sql
SELECT * FROM users
WHERE username='' OR ''=''
AND password='' OR ''='';
```

which would match all user records.

## Batched Statements

Since SQL supports batched statements that can be exploited. Consider the
following query

```sql
SELECT * FROM users
WHERE username=entered_username;
```

By injecting `1; DROP TABLE *` this query becomes

```sql
SELECT * FROM users
WHERE username=1; DROP TABLE *;
```
