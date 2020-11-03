# Functions

Loadmill has builtin functions available to use while creating a test. These functions will be evaluated in run time as part of the test.

## Numeric Functions

### `__abs(p1)`

Returns the absolute value of `p1`.

* `${__abs('-42')} // returns 42`
* `${__abs(p1)} // returns 42, assuming parameter p1 equlas 42`

### `__add(p1,[p2,[...]])`

Same as the `+` operator, applied to any number of arguments.

* `${__add('42','3')} // returns 45`
* `${__add(p1,p2)} // returns 10, assuming p1 is 7 and p2 is 3`
* `${__add(p1,p2,p3)} // returns 15, assuming p1 is 7, p2 is 3 and p3 is 5`

### `__sub(p1,p2)`

Same as the `-` operator.

* `${__sub('42','3')} // returns 39`
* `${__sub(p1,p2)} // returns 4, assuming p1 is 7 and p2 is 3`
* `${__sub(p1,p2,p3)} // returns 3, assuming p1 is 7, p2 is 3 and p3 is 1`

### `__neg(p1)`

Unary minus, equivalent to `__sub('0',p1)`.

* `${__neg('4')} // returns -4`
* `${__neg('-4')} // returns 4`
* `${__neg(p1)} // returns -4, assuming p1 is 4`

### `__mult(p1,[p2,[...]])`

Same as the `*` operator, applied to any number of arguments.

* `${__mult('2','3')} // returns 6`
* `${__mult(p1,p2,p3)} // returns 24 assuming p1 is 2, p2 is 3 and p3 is 4`

### `__div(p1,p2)`

Same as the `/` operator.

* `${__div('6','3')} // returns 2`
* `${__div(p1,p2} // returns 4 assuming p1 is 24 and p2 is 6`

## Conditional Functions

### `__true()`

Always returns `true`.

### `__false()`

Always returns `false`.

### `__and(p1,[p2,[...]])`

* `${__and('true','true')} // returns true`
* `${__and('true','false')} // returns false`
* `${__and('true','')} // returns false`
* `${__and(p1,p2)} // returns true, assuming p1 and p2 aren't false nor ''`
* `${__and()} // returns true`
* `${__and('-42')} // returns true`

Logical AND \(same as the `&` operator\), applied to any number of arguments.

### `__or(p1,[p2,[...]])`

Logical OR \(same as the `|` operator\), applied to any number of arguments.

* `${__or('true','true')} // returns true`
* `${__or('true','false')} // returns true`
* `${__or('false','false')} // returns false`
* `${__or('','false')} // returns false`
* `${__or(p1,p2)} // returns true, assuming p1 or p2 aren't false nor ''`
* `${__or()} // returns true`
* `${__or('-42')} // returns true`

### `__not(p1)`

Logical NOT. See also [True Semantics](parameters.md#true-semantics).

* `${__not('false')} // returns true`
* `${__not('true')} // returns false`
* `${__not('')} // returns true`
* `${__not(p1)} // returns true, assuming p1 is't false nor ''`
* `${__not('-42')} // returns false`

### `__eq(p1,p2)`

Same as the `=` operator.

* `${__eq('42','3')} //returns false`
* `${__eq('false','false')} //returns true`
* `${__eq('FaLsE','false')} //returns false`
* `${__eq('','')} //returns true`
* `${__eq(p1,p2)} //returns true if both p1 and p2 have the same value`

### `__neq(p1,p2)`

Same as the `!=` operator.

* `${__neq('42','3')} //returns true`
* `${__neq('false','false')} //returns false`
* `${__neq('FaLsE','false')} //returns true`
* `${__neq('','')} //returns false`
* `${__neq(p1,p2)} //returns true if both p1 and p2 have a different value`

### `__eqi(p1,p2)`

Same as `__eq` but case-insensitive.

* `${__eqi('42','3')} //returns false`
* `${__eqi('false','false')} //returns true`
* `${__eqi('FaLsE','false')} //returns true`
* `${__eqi('','')} //returns true`
* `${__eqi(p1,p2)} //returns true if both p1 and p2 have the same value`

### `__neqi(p1,p2)`

Same as `__neq` but case-insensitive.

* `${__neq('42','3')} //returns true`
* `${__neq('false','false')} //returns false`
* `${__neq('FaLsE','false')} //returns false`
* `${__neq('','')} //returns false`
* `${__neq(p1,p2)} //returns true if both p1 and p2 have a different value`

### `__lt(p1,p2)`

Same as the `<` operator.

* `${__lt('42','3')} //returns false`
* `${__lt('3','42')} //returns true`
* `${__lt('42','42')} //returns false`
* `${__lt(p1,p2)} //returns true, assuming p1 is 3 and p2 is 42` 

### `__lte(p1,p2)`

Same as the `<=` operator.

* `${__lte('42','3')} //returns false`
* `${__lte('3','42')} //returns true`
* `${__lte('42','42')} //returns true`
* `${__lte(p1,p2)} //returns true, assuming p1 is 3 and p2 is 42` 

### `__gt(p1,p2)`

Same as the `>` operator.

* `${__gt('42','3')} //returns true`
* `${__gt('3','42')} //returns false`
* `${__gt('42','42')} //returns false`
* `${__gt(p1,p2)} //returns true, assuming p1 is 42 and p2 is 3` 

### `__gte(p1,p2)`

Same as the `>=` operator.

* `${__gte('42','3')} //returns true`
* `${__gte('3','42')} //returns false`
* `${__gte('42','42')} //returns true`
* `${__gte(p1,p2)} //returns true, assuming p1 is 42 and p2 is 3` 

### `__matches(target,regex)`

Returns `true` if and only if the `target` matches the `regex`.

* `${__matches(target,'.*search.*')} // returns true, assuming target is  'A text to search in'`

### `__contains(target,search)`

Returns `true` if and only if the `target` contains the string `search`.

* `${__contains(target,'search')} // returns true, assuming target is  'A text to search in'`
* `${__contains(target,'SEARCH')} // returns false, assuming target is  'A text to search in'`
* `${__contains(target,'.*search.*')} // returns false, assuming target is  'A text to search in'`

### `__containsi(target,search)`

Same as `__contains` but case-insensitive.

* `${__containsi(target,'search')} // returns true, assuming target is  'A text to search in'`
* `${__containsi(target,'SEARCH')} // returns true, assuming target is  'A text to search in'`
* `${__containsi(target,'.*search.*')} // returns false, assuming target is  'A text to search in'`

### `__if_then_else(condition,then,else)`

Returns `then` if `condition` is [semantically true](parameters.md#true-semantics), otherwise returns `else`.

* `${__if_then_else(p1,'good','bad')} // returns 'good', assuming p1 is true or has a value`
* `${__if_then_else(p1,'good','bad')} // returns 'bad', assuming p1 is false or  ''`

### `__is_number(target)`

Returns true if target is not empty and not a NAN.

* `${__is_number('42')} // returns true`
* `${__is_number('')} // returns false`
* `${__is_number('Hi')} // returns false`
* `${__is_number(p1)} // returns true assuming p1 is a number i.e. 42`

### `__is_uuid(target)`

Returns true if target is in the format of UUID.

* `${__is_uuid('123e4567-e89b-12d3-a456-426614174000')} // returns true`
* `${__is_uuid('42')} // returns false`

### `__switch(target,case1,value1,[case2,value2,[...],[default]])`

Returns `value1` if `target` equals `case1`, otherwise returns `value2` if `target` equals `case2` and so on.

If no match is made, the returned value will be an empty string - a default value may be given as the last argument.

* `${__switch(p1,'3','Hi','42','towel','none')} // returns 'Hi' if p1 is 3, 'towel' if p1 is 42 and 'none' if p1 is neither 3 nor 42`

### `__switchi(target,case1,value1,[case2,value2,[...],[default]])`

Same as `__switch` but case-insensitive.

* `${__switchi(p1,'this','Hi','that','towel','none')} // returns 'Hi' if p1 is 'this' or 'THIS', 'towel' if p1 is 'that' or 'THAT' and 'none' if p1 is neither of those`

### `__pick(selection,p1,[p2,[...]])`

Returns one of `p1` or `p2` or `p3`, etc. according to the `selection` - either a zero-based index \(e.g. `2` picks `p3`\) or the word `random` in order to pick a random value.

* `${__pick('0','A','B','C')} // returns 'A'`
* `${__pick('1','A','B','C')} // returns 'B'`
* `${__pick(p1,'A','B','C')} // returns 'C', assuming p1 is 2`
* `${__pick('random','A','B','C')} // returns one of 'A', 'B' and 'C'`

### `__pick_random(p1,[p2,[...]])`

Same as `__pick('random',p1,[p2,[...]])`.

### `__split_pick(target,delim,[selection=0])`

Splits the value of `target` into multiple strings separated by `delim` and returns one of them according to the `selection` as defined by the `__pick` function. If a `selection` argument is not provided, the first value will be returned.

* `${__split_pick(p1,'API')} // returns 'loadmill' , assuming p1 value is 'loadmill API testing'`
* `${__split_pick(p1,'API','0')} // returns 'loadmill' , assuming p1 value is 'loadmill API testing'`
* `${__split_pick(p1,'API','1')} // returns 'testing' , assuming p1 value is 'loadmill API testing'`

#### Textual Functions

### `__usd()`

Returns the `$` character.

### `__length(target)`

Counts the number of characters in `target`.

* `${__length('loadmill')} // returns 8`
* `${__length('')} // returns 0`

### `__array_length(target)`

Counts the number of elements in `target` array.

* `${__array_length('[]')} // returns 0`
* `${__array_length(p1)} // returns 4, assuming p1 is [1,"str",true,null]`

### `__escape_regexp(target)`

Returns the value of `target` after escaping special RegExp characters.

* `${__escape_regexp('.*search.*')} // returns \.\*search\.\*`

### `__encode_url(target)`

Returns the value of `target` after [URL encoding](https://en.wikipedia.org/wiki/Percent-encoding) special characters.

* `${__encode_url(p1)} // returns 'this%20is%20url' assuming p1 is 'this is url'`

### `__decode_url(target)`

Returns the value of `target` after [URL decoding](https://en.wikipedia.org/wiki/Percent-encoding).

* `${__decode_url(p1)} // returns 'this is url' assuming p1 is 'this%20is%20url'`

### `__escape_quotes(target)`

Returns the value of `target` after escaping special characters. This functions like escape quotes in JavaScript and will escape characters like \n \r \t and \".

* `${__escape_quotes('"escapeMe"')} // returns \"escapeMe\"`
* `${__escape_quotes(P1)} // returns \"escapeMe\", assuming p is 'escapeMe'`

### `__lower(target)`

Returns the value of `target` after converting all characters to lower case.

* `${__lower('LoadMill')} // returns loadmill`

### `__upper(target)`

Returns the value of `target` after converting all characters to upper case.

* `${__upper('LoadMill')} // returns LOADMILL`

### `__slice(target,[begin=0,[end]])`

Returns a sub-string of `target` which starts at `begin` index \(inclusive\) and ends at `end` index \(exclusive\). Both indexes are zero-based.

* `${__slice('Loadmill')} // returns 'Loadmill'`
* `${__slice('Loadmill','0')} // returns 'Loadmill'`
* `${__slice('Loadmill','2')} // returns 'admill'`
* `${__slice('Loadmill','2','4')} // returns 'ad'`
* `${__slice('Loadmill',p1,p2)} // returns 'mill', assuming p1 is 4 and p2 is 8`

## Extraction Functions

See also [Parameter Extractions](parameters.md#parameter-extraction).

### `__regexp(target,regexp,[default])`

Extracts a value from `target` using `regexp` as a JS RegExp. If there is no match, an empty string will be returned or, if present, the given `default` value.

* `${__regexp(p1,'.*(search).*')} // returns 'search' assuming p1 is 'A text to search in'`
* `${__regexp(p1,'(.*search.*)')} // returns 'A text to search in' assuming p1 is 'A text to search in'`
* `${__regexp(p1,'.*(bad).*','none')} // returns 'none' assuming p1 is 'A text to search in'`

### `__jsonpath(target,jsonpath,[default])`

Extracts a value from `target` using `jsonpath` as a JSONPath query. If there is no match, an empty string will be returned or, if present, the given `default` value.

* `${__jsonpath('{"key":"val"}','$.key')} // returns 'val'`
* `${__jsonpath(p1,jsonpath)} // returns 'val' assuming p1 is  and jsonpath is '$.key'`
* `${__jsonpath('{"key":"val"}','$.notHere','none')} // returns 'none'`

#### `__jquery(target,jquery,[selection=0,[attribute,[default]]])`

Extracts a value from `target` using `jquery` as a jQuery selector.

If multiple elements are matched, `selection` is applied as in `__pick` with the first element being selected by default.

If a non-empty `attribute` is given, the returned value will be the attribute value of the selected element, otherwise, the inner content of the element will be returned.

If there is no match, an empty string will be returned or, if present, the given `default` value.

* `${__jquery('<h2 class="title">Hello world</h2>','h2.title')} //returns Hello world`
* `${__jquery(p1,jquery)} //returns Hello world, assuming p1 is '<h2 class="title">Hello world</h2>' and jquery is h2.title`

## Randomization Functions

### `__random_uuid()`

Returns a random v4 UUID string.

### `__random_boolean([probability=50])`

Returns a random boolean value. You may pass an integer between 0 and 100 as the `probability` to get `true` - defaults to 50%.

* `${__random_boolean()} // 50% true / false`
* `${__random_boolean('70')} // returns true 70% of the times`
* `${__random_boolean(p1)} // returns true 20% of the times, assuming p1 is 20`

### `__random_number([max],[min=0,max=2^32])`

Returns a random integer between 0 and 2^32. By passing a positive integer you can set a lower maximum, e.g. `__random_number('30')` will resolve to a number between 0 and 30, inclusive. You can also set the minimum, e.g. `__random_number('10','30')` will be between 10 and 30, inclusive.

* `${__random_number('30')} // returns a number between 0 and 30`
* `${__random_number('10','30')} // returns a number between 10 and 30`
* `${__random_number(p1)} // returns a number between 0 and the value of p1`

### `__random_chars([length=10])`

Returns a random string of `length` alpha-numeric characters.

* `${__random_chars('5')} // returns g2Niu`
* `${__random_chars()} // returns YIeT6JXgbJ`
* `${__random_chars(p1)} // returns YXgbT, assuminp1 is 5`

### `__random_digits([length=10])`

Returns a random string of `length` decimal digits.

* `${__random_digits('5')} // returns 83547`
* `${__random_digits()} // returns 8354718624`
* `${__random_digits(p1)} // returns 83524, assuming p1 is 5`

### `__random_letters([length=10])`

Returns a random string of `length` english letters.

* `${__random_letters()} // returns YMfvLoYhjh`
* `${__random_letters('5')} // returns diMdf`
* `${__random_letters(p1)} // returns diMdf, assuming p1 is 5`

### `__random_uppers([length=10])`

Returns a random string of `length` upper-case english letters.

* `${__random_uppers()} // returns STNOMFSLZC`
* `${__random_uppers('5')} // returns WPVRA`
* `${__random_uppers(p1)} // returns WPVRA, assuming p1 is 5`

### `__random_lowers([length=10])`

Returns a random string of `length` lower-case english letters.

* `${__random_uppers()} // returns osmcjtudhe`
* `${__random_uppers('5')} // returns alrmv`
* `${__random_uppers(p1)} // returns alrmv, assuming p1 is5`

### `__random_hex([length=10])`

Returns a random string of `length` hexadecimal digits.

* `${__random_hex()} // returns d8c3f7ce22`
* `${__random_hex('5')} // returns e5a4b`
* `${__random_hex(p1)} // returns e5a4b, assumin p1 is 5`

### `__random_from(chars,[length=10])`

Returns a random string of `length` characters present in `chars`. For example, you may generate a random **uppercase** hexadecimal string using `__random_from('0123456789ABCDEF')`.

* `__random_from('0123456789ABCDEF') // returns 313249C4FA`
* `__random_from('Loadmill') // returns lilodaaLod`
* `__random_from(p1) // returns lilodaaLod, assuming p1 is 'Loadmill'`
* `__random_from('Loadmill','3') // returns ido`

## Time Functions

### `__now()`

Returns the current time \(of evaluation\) given as UTC milliseconds. Alias: `_now_ms`.

* `${__now()} // returns 1604422320167`
* `${'Yo'} ${__now()} // returns 'Yo 1604422320167'`

### `__now_iso([addedMinutes=0])`

The same as `__now` but given in ISO-8601 format while adding `addedMinutes` . For example,  you may generate the current time + 15 minutes using `__now_iso('15')`.

* `${__now_iso()} // returns 2020-11-03T16:54:24.526Z`
* `${__now_iso('15')} // returns 2020-11-03T17:09:24.526Z`
* `${__now_iso('-15')} // returns 2020-11-03T16:39:24.526Z`

### **`__date_iso()`**

The same as `__now_iso` but given in a "date only" format - i.e. `2020-03-03`

* `${__date_iso()} // returns 2020-11-03`
* `${__date_iso('15')} // returns 2020-11-18`
* `${__date_iso('-15')} // returns 2020-10-19`

