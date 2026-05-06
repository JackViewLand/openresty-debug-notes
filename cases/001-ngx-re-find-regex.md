# Case 001 - ngx.re.find regex pitfalls

## Problem

A User-Agent string failed to match correctly when using `ngx.re.find`.

Example:

k6/0.56.0 (https://k6.io/)

## Root Cause

ngx.re.find uses regex patterns, not shell wildcard matching.

Special characters such as ., (, and ) must be escaped.

## Wrong Pattern
```
k6/0.56.0 (https://k6.io/)
```
## Correct Pattern
```
k6/0\.56\.0 \(https://k6\.io/\)
```
## Lesson Learned

Always confirm whether the matching logic expects:

* regex
* wildcard
* plain string