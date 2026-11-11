# Day 6 Project — Reusable Python Logging and Timing Utility

## Objective
Build a decorator that measures function duration and logs safe execution events. Practise decorators, functools.wraps, type hints and logging.

## Create timing_utils.py
~~~python
import logging
import time
from functools import wraps
from typing import Callable, TypeVar, Any

F = TypeVar("F", bound=Callable[..., Any])
logging.basicConfig(level=logging.INFO, format="%(levelname)s %(message)s")


def timed(function: F) -> F:
    @wraps(function)
    def wrapper(*args: Any, **kwargs: Any) -> Any:
        start = time.perf_counter()
        logging.info("Starting %s", function.__name__)
        try:
            return function(*args, **kwargs)
        finally:
            elapsed = time.perf_counter() - start
            logging.info("%s completed in %.6f seconds", function.__name__, elapsed)
    return wrapper  # type: ignore[return-value]


@timed
def process_questions(questions: list[str]) -> list[str]:
    return [question.strip().lower() for question in questions if question.strip()]


if __name__ == "__main__":
    result = process_questions(["  What is RAG? ", "", "Explain agents"])
    print(result)
~~~

## Explanation
- perf_counter() is a high-resolution monotonic timer for elapsed duration.
- wraps preserves the decorated function's metadata.
- wrapper accepts arbitrary positional and keyword arguments.
- try/finally ensures duration is logged even if the wrapped function raises.
- return passes the original result to the caller.
- TypeVar and Callable describe the callable type. The type-ignore comment acknowledges a limitation in static inference for generic wrappers.

## Run
Windows: py timing_utils.py  
macOS/Linux: python3 timing_utils.py

Expected result: ['what is rag?', 'explain agents'] plus start and duration log entries.

## Tests
| Case | Expected |
|---|---|
| Two valid questions | Two cleaned strings |
| Blank item | Excluded |
| Empty list | Empty list |
| Wrapped function raises | Exception propagates and duration is logged |
| Inspect __name__ | Remains process_questions |

## Extensions
1. Write a generator yielding cleaned lines.
2. Add a decorator that counts calls.
3. Explain why elapsed duration uses perf_counter.
4. Add type hints to another function.

## Submission
Submit source, sample output, test results and an explanation of yield, wrapper and finally.
