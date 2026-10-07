# Plan for issue #53

Issue: https://github.com/codepath/pathreview-ai301-fa26-s3/issues/53

## Reproduction evidence

I tested commit 2f4e82f52efbcfcc57d65b3fa5348672163ca088
on Windows with Python 3.13.0, pytest 9.1.1, and structlog 26.1.0.

For the input `Call me at (555) 123-4567`:
- scrub() returned the text unchanged.
- detect() returned an empty list.

Running the existing test file produced 20 passed and 5 xfailed.
Running with --runxfail produced 20 passed and 5 failed.

Four failures concern phone-number handling. The fifth,
test_mixed_pii_and_text, fails because the street-address pattern
incorrectly matches `5 years developing Python appl`.
That is a separate problem.

## Diagnosis

The US phone-number pattern does not allow the space between
the closing parenthesis and the next three digits.

Its leading word boundary also prevents a match from starting
at the opening parenthesis after a space or at the start of text.

Both scrub() and detect() use this pattern, so I will check
that the updated pattern matches the complete phone number.

## Scope

Update the US phone-number pattern in safety/pii_scrubber.py
and the relevant tests in tests/unit/test_pii_scrubber.py.

Preserve supported dashed, dotted, and country-code formats.

Leave the street-address pattern and its separate failing
mixed-text test unchanged.

## Approach

1. Update PIIScrubber.PII_PATTERNS["phone_us"] to support
   parenthesized area codes and spaces between number groups.
2. Check boundaries so the pattern does not match part of
   a longer number or an identifier.
3. Strengthen focused tests to check full redaction and
   the complete detected value and its positions.
4. Remove the four phone-specific xfail markers once those
   tests pass. Keep the mixed-text marker.

## Test plan

Repeat the original input. Expected:
- scrub(): `Call me at [REDACTED]`
- detect(): a phone_us match containing `(555) 123-4567`,
  starting at position 11 and ending at position 25.

Check parenthesized numbers at the beginning and end of text,
plus dashed, dotted, and +1 formats.

Check that longer digit strings and identifiers do not
produce partial US phone-number matches.

Run the complete PII scrubber test file. The phone tests
should pass, existing passing tests should remain passing,
and the separate mixed-text test should remain xfailed.

Record the actual commands and results after implementation.

## Risks and unknowns

Changing boundaries or allowing spaces could introduce false
positives. I will test those cases before calling the fix complete.

The international phone pattern may overlap with +1 inputs.
I will check the full redacted output and detected values.

## Deviations

Implementation has not started. I will record any changes
to this plan after building and testing.