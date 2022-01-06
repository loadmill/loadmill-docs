# ⨍(⨯) FUNCTIONS

Loadmill has builtin functions available to use while creating a test. These functions will be evaluated in run time as part of the test.

## Numeric Functions

### `__abs(p1)`

Returns the absolute value of `p1`.

* `${__abs('-42')} // returns 42`
* `${__abs(p1)} // returns 42, assuming parameter p1 equals 42`

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

Logical AND (same as the `&` operator), applied to any number of arguments.

### `__or(p1,[p2,[...]])`

Logical OR (same as the `|` operator), applied to any number of arguments.

* `${__or('true','true')} // returns true`
* `${__or('true','false')} // returns true`
* `${__or('false','false')} // returns false`
* `${__or('','false')} // returns false`
* `${__or(p1,p2)} // returns true, assuming p1 or p2 aren't false nor ''`
* `${__or()} // returns true`
* `${__or('-42')} // returns true`

### `__not(p1)`

Logical NOT. See also [True Semantics](parameters/#true-semantics).

* `${__not('false')} // returns true`
* `${__not('true')} // returns false`
* `${__not('')} // returns true`
* `${__not(p1)} // returns true, assuming p1 is't false nor ''`
* `${__not('-42')} // returns false`

### `__eq(p1,p2)`

Same as the `==` operator.

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

* `${__matches(target,'.*search.*')} // returns true, assuming target is 'A text to search in'`

### `__contains(target,search)`

Returns `true` if and only if the `target` contains the string `search`.

* `${__contains(target,'search')} // returns true, assuming target is 'A text to search in'`
* `${__contains(target,'SEARCH')} // returns false, assuming target is 'A text to search in'`
* `${__contains(target,'.*search.*')} // returns false, assuming target is 'A text to search in'`

### `__containsi(target,search)`

Same as `__contains` but case-insensitive.

* `${__containsi(target,'search')} // returns true, assuming target is 'A text to search in'`
* `${__containsi(target,'SEARCH')} // returns true, assuming target is 'A text to search in'`
* `${__containsi(target,'.*search.*')} // returns false, assuming target is 'A text to search in'`

### `__if_then_else(condition,then,else)`

Returns `then` if `condition` is [semantically true](parameters/#true-semantics), otherwise returns `else`.

* `${__if_then_else(p1,'good','bad')} // returns 'good', assuming p1 is true or has a value`
* `${__if_then_else(p1,'good','bad')} // returns 'bad', assuming p1 is false or ''`

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

Returns one of `p1` or `p2` or `p3`, etc. according to the `selection` - either a zero-based index (e.g. `2` picks `p3`) or the word `random` in order to pick a random value.

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

## Textual Functions

### `__usd()`

Returns the `$` character.

### `__length(target)`

Counts the number of characters in `target`.

* `${__length('loadmill')} // returns 8`
* `${__length('')} // returns 0`

### `__escape_regexp(target)`

Returns the value of `target` after escaping special RegExp characters.

* `${__escape_regexp('.*search.*')} // returns \.\*search\.\*`

### `__encode_url(target)`

Returns the value of `target` after [URL encoding](https://en.wikipedia.org/wiki/Percent-encoding) special characters.

* `${__encode_url(p1)} // returns 'this%20is%20url' assuming p1 is 'this is url'`

### `__decode_url(target)`

Returns the value of `target` after [URL decoding](https://en.wikipedia.org/wiki/Percent-encoding).

* `${__decode_url(p1)} // returns 'this is url' assuming p1 is 'this%20is%20url'`

### `__encode_base64(target)`

Returns the value of `target` after [Base64](https://en.wikipedia.org/wiki/Base64) encoding.

* `${__encode_base64(p1)} // returns 'ZXhhbXBsZQ==' assuming p1 is 'example'`

### `__decode_base64(target)`

Returns the value of `target` after [Base64](https://en.wikipedia.org/wiki/Base64) decoding.

* `${__decode_base64(p1)} // returns 'example' assuming p1 is 'ZXhhbXBsZQ=='`

### `__escape_quotes(target)`

Returns the value of `target` after escaping special characters. This function is like escape quotes in JavaScript and will escape characters like \n \r \t and \\".

* `${__escape_quotes('"escapeMe"')} // returns \"escapeMe\"`
* `${__escape_quotes(P1)} // returns \"escapeMe\", assuming p is "escapeMe"`

### `__lower(target)`

Returns the value of `target` after converting all characters to lower case.

* `${__lower('LoadMill')} // returns loadmill`

### `__upper(target)`

Returns the value of `target` after converting all characters to upper case.

* `${__upper('LoadMill')} // returns LOADMILL`

### `__slice(target,[begin=0,[end]])`

Returns a sub-string of `target` which starts at `begin` index (inclusive) and ends at `end` index (exclusive). Both indexes are zero-based.

* `${__slice('Loadmill')} // returns 'Loadmill'`
* `${__slice('Loadmill','0')} // returns 'Loadmill'`
* `${__slice('Loadmill','2')} // returns 'admill'`
* `${__slice('Loadmill','2','4')} // returns 'ad'`
* `${__slice('Loadmill',p1,p2)} // returns 'mill', assuming p1 is 4 and p2 is 8`
* `${__slice(p1,'0','2')} // returns 'Lo', assuming p1 is Loadmill`

## Array functions

### `__array_length(target)`

Counts the number of elements in `target` array.

* `${__array_length('[]')} // returns 0`
* `${__array_length(p1)} // returns 4, assuming p1 is [1,"str",true,null]`

### `__array_matches(target,regex)`

Returns a boolean string of whether all the elements in the target array match the given regex.

* `${__array_matches(array,'.*a.*')} // returns true, assuming array is ["apple","banana","orange"]`
* `${__array_matches(array,'.*Z.*')} // returns false, assuming array is ["apple","banana","orange"]`

### `__array_in_range(target,[min=0,max=2^32])`

Returns a boolean string of whether all the elements in the target array match the given range.

* `${__array_in_range(array,'0','100')} // returns true, assuming array is ["100","99","1"]`
* `${__array_in_range(array,'0','100')} // returns true, assuming array is [100,99,1]`

### **`__array_includes(src,target)`**

Returns a boolean string of whether each element in the target array is also in the src array.

* `${__array_includes(srcArray,targetArray)} // returns true, assuming srcArray is ["apple","banana","orange"] and targetArray is ["apple","banana"]`
* `${__array_includes(srcArray,targetArray)} // returns false, assuming srcArray is ["apple","banana","orange"] and targetArray is ["apple","banana","lemon"]`

### `__array_sum(target)`

Returns the sum of all the elements in the target array.

* `${__array_sum(targetArray)} // returns 401, assuming targetArray is ["400","0","1"]`
* `${__array_sum(targetArray)} // returns 188, assuming targetArray is [100,80,8]`
* `${__array_sum(targetArray)} // returns NaN, assuming targetArray is [100,"some-word",8]`

### `__array_sort(target)`

Returns the sorted array in the ascending order.

* `${__array_sort(targetArray) // returns ["apple","banana","orange"], assuming targetArray is ["banana","apple","orange"]`

### `__array_sort_numbers(target)`

Returns the sorted array of numbers in the ascending order.

* `${__array_sort_numbers(targetArray) // returns [2,19,34,55,90,109,136,156,188,190], assuming targetArray is [109, 136, 156, 188, 19, 190, 2, 34, 55, 90]`

### `__array_is_unique(target)`

Returns a boolean string of whether all elements in the array are unique.

* `${__array_is_unique(targetArray) // returns true, assuming targetArray is ["cat","dog","bird"]`
* `${__array_is_unique(targetArray) // returns false, assuming targetArray is ["cat","cat","dog"]`

### `__array_pluck(target,'key1','key2','key3:newKeyName',['key4',[...]])`

Returns an array of objects with specified JSON keys with an option to rename JSON keys. Returns an empty array in case the target array is undefined.

* `${__array_pluck(array,'author','book')} // returns [{"author":"Bulgakov","book":"The Master and Margarita"},{"author":"Bulgakov","book":"The Fatal Eggs"}], assuming array is [{"author":"Bulgakov","book":"The Master and Margarita","year":"1967"},{"author":"Bulgakov","book":"The Fatal Eggs","year":"1925"}]`
* `${__array_pluck(array,'author','book','year:publishment_year')} // returns [{"author":"Bulgakov","book":"The Master and Margarita","publishment_year":"1967"},{"author":"Bulgakov","book":"The Fatal Eggs","publishment_year":"1925"}], assuming array is [{"author":"Bulgakov","book":"The Master and Margarita","year":"1967"},{"author":"Bulgakov","book":"The Fatal Eggs","year":"1925"}]`

## **Extraction Functions**

See also [Parameter Extractions](parameters/#parameter-extraction).

### `__regexp(target,regexp,[default])`

Extracts a value from `target` using `regexp` as a JS RegExp. If there is no match, an empty string will be returned or, if present, the given `default` value.

* `${__regexp(p1,'.*(search).*')} // returns 'search' assuming p1 is 'A text to search in'`
* `${__regexp(p1,'(.*search.*)')} // returns 'A text to search in' assuming p1 is 'A text to search in'`
* `${__regexp(p1,'.*(bad).*','none')} // returns 'none' assuming p1 is 'A text to search in'`

### `__json_keys(target,[default])`

Returns the keys of target object in an array. Works similar to [Object.keys](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Object/keys). If `target` is empty, an empty array will be returned or, if present, the given `default` value.

* `${__json_keys('{"key1":"val1"}')}// returns ["key1"]`
* `${__json_keys(target)} // returns ["key1","key2"] assuming target is {"key1":"val1","key2":"val2"}`

### `__jsonpath(target,jsonpath,[default])`

Extracts a value from `target` using `jsonpath` as a JSONPath query. If there is no match, an empty string will be returned or, if present, the given `default` value.

* `${__jsonpath('{"key":"val"}','$.key')} // returns 'val'`
* `${__jsonpath(target,jsonpath)} // returns 'val' assuming target is '{"key":"val"}' and jsonpath is '$.key'`
* `${__jsonpath('{"key":"val"}','$.notHere','none')} // returns 'none'`

### `__jsonpath_all(target,jsonpath)`

Similar to `__jsonpath` but returns **all results from the JSONPath** and not only one as happens when using `__jsonpath.`

### `__jsonpath_keys(target,jsonpath)`

Returns the keys of the extracted value from `target` queried by `jsonpath` in an array. Works similar to [Object.keys](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Object/keys).

* `${__jsonpath_keys('{"key1":"val1"}','$')}// returns ["key1"]`
* `${__jsonpath_keys(target,jsonpath)} // returns ["key1","key2"] assuming target is {"data": {"key1":"val1","key2":"val2"}} and jsonpath is '$.data'`

### `__jsonpath_apply(target,jsonpath,new_value)`

Returns an object or an array of objects with the updated key value as set in `new_value` on specific key as set in `jsonpath`.

* `${__jsonpath_apply(target,jsonpath,'USD')} // returns '[{"country":"Japan","currency":"USD"},{"country":"China","currency":"Yuan"}]' assuming target is '[{"country":"Japan","currency":"Yen"},{"country":"China","currency":"Yuan"}]', jsonpath is '$[0].currency' and new_value is 'USD'.`

### `__jquery(target,jquery,[selection=0,[attribute,[default]]])`

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
* `${__random_chars(p1)} // returns YXgbT, assuming p1 is 5`

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

* `${__random_lowers()} // returns osmcjtudhe`
* `${__random_lowers('5')} // returns alrmv`
* `${__random_lowers(p1)} // returns alrmv, assuming p1 is5`

### `__random_hex([length=10])`

Returns a random string of `length` hexadecimal digits.

* `${__random_hex()} // returns d8c3f7ce22`
* `${__random_hex('5')} // returns e5a4b`
* `${__random_hex(p1)} // returns e5a4b, assuming p1 is 5`

### `__random_from(chars,[length=10])`

Returns a random string of `length` characters present in `chars`. For example, you may generate a random **uppercase** hexadecimal string using `__random_from('0123456789ABCDEF')`.

* `__random_from('0123456789ABCDEF') // returns 313249C4FA`
* `__random_from('Loadmill') // returns lilodaaLod`
* `__random_from(p1) // returns lilodaaLod, assuming p1 is 'Loadmill'`
* `__random_from('Loadmill','3') // returns ido`

### `__random_seeded_number([seed='',length=10])`

Returns a random string of up to `length` (but no more than 10) decimal digits based on a given seed. Same seed will return the same number.

* `__random_seeded_number() // returns 994027583`
* `__random_seeded_number('0123456789ABCDEF') // returns 2082602645`
* `__random_seeded_number('0123456789ABCDEF','5') // returns 20826`

## Hash Functions

### `__sha1(secret,[secretFormat='utf-8'])`

Creating hash digests of data using an algorithm of `sha1`. The function returns a hash in hexadecimal digits. Supported secretFormats are `utf-8` and `hex`.

* `${__sha1('mySecret')} alias ${__sha1('mySecret','utf-8')}`&#x20;
* `${__sha1('mySecret','hex')}`
* `${__sha1(p1,p2) assuming p1 contains your secret and p2 - your secretFormat.`

### `__sha256(secret,[secretFormat='utf-8'])`

Creating hash digests of data using an algorithm of `sha256`. The function returns a hash in a hexadecimal digits. Supported secretFormats are `utf-8` and `hex`.

* `${__sha256('mySecret')} alias ${__sha256('mySecret','utf-8')}`&#x20;
* `${__sha256('mySecret','hex')}`
* `${__sha256(p1,p2) assuming p1 contains your secret and p2 - your secretFormat.`

## Time Functions

### `__now([length=13])`

Returns the current time (of evaluation) given as UTC milliseconds of `length` digits. Alias: `_now_ms`.

* `${__now()} // returns 1604422320167`
* `${__now('5')} // returns 16044`
* `${'Yo'} ${__now()} // returns 'Yo 1604422320167'`

### `__now_iso([addedMinutes=0])`

The same as `__now` but given in ISO-8601 format while adding `addedMinutes` . For example, you may generate the current time + 15 minutes using `__now_iso('15')`.

* `${__now_iso()} // returns 2020-11-03T16:54:24.526Z`
* `${__now_iso('15')} // returns 2020-11-03T17:09:24.526Z`
* `${__now_iso('-15')} // returns 2020-11-03T16:39:24.526Z`

### **`__date_iso()`**

The same as `__now_iso` but given in a "date only" format - i.e. `2020-03-03`

* `${__date_iso()} // returns 2020-11-03`
* `${__date_iso('15')} // returns 2020-11-18`
* `${__date_iso('-15')} // returns 2020-10-19`
