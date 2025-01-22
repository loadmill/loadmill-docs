# Extraction & Assertion step

The extraction & assertion step allows extracting, assigning parameters and add validations without spinning an entire request. Among it's usages are assigning or allocating values at the beginning of a flow of after calling a generic shared flow and we need to extract/re-assign/validate additional flow specific data.

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

The Extract & Assert step consists of three main areas:

1.  Extraction section - a place to assign and extract the parameters.\
    Note that the extractions will refer to the last response that was introduced, ie. the previous response.\


    <figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

    Each extraction consists of three parts:

    1. Parameter name - the name that the parameter will be referenced when used, this filed can accept letters, numbers and undescores (\`\_\`).
    2. Assignment method/type - A selection of methods that can be used to acquire the value for the parameter. The available methods are: Assign, JSONPath, Clojure, xPath, RegExp, Header and WebSocket. For detailed explanation about each one of the methods please refer to the [Extractions documentation](../../general/api-testing1/test-suite-editor/set-parameters-extractions.md).
2.  Assertions area - A place for data validations (Assertions)

    <figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

    The assertions section consists of three areas:

    1. The parameter that carries the value for the validation.
    2. The comparison method (the operator), also referred as the value, the available operators are\
       Exists, Doesn't exists, Equals, Doesn't equals, Contains, Doesn't contains, Matches, Greater than, Less than, JSON Schema, JSON Contains, XML Contains.\
       For detailed explanation about each one of the comparison methods please refer to the [Assertions documentation](../../general/api-testing1/test-suite-editor/assertions.md).
    3. The expression - when applicable, this value will carry the compared value or expression for the validation.
3. Flow control area - Allows skipping to another step, stopping the flow and add wait time after step execution.
