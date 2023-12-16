A bash script `verify-jq.sh` to approval-test jq code.

# Install

Download `verify-jq.sh`, `chmod +x verify-jq.sh` and make available on `PATH`.

## Requirements

-   `bash`
-   `diff`
-   `jq`

# Writing Tests

-   Test files adhere to this pattern: `test_*.jq`
-   Test functions start with `test_`
-   Test functions return JSON to be verified by the runner

## Example

```jq
# test_example.jq

def test_something:
    "Verify me!";
```

## Separating Production Code from Test Code

```jq
# fizzbuzz.jq

def fizzbuzz:
    if . == 3 "Fizz"
    else .
    end;
```

```jq
# test_fizzbuzz.jq

include "fizzbuzz";

def test_fizzbuzz_range_1_10:
    range(10) + 1 | fizzbuzz;
```

# Running

```shell
cd tests
verify-jq.sh
```
