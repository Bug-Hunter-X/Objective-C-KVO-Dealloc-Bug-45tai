# Objective-C KVO Dealloc Bug

This repository demonstrates a common but subtle bug in Objective-C related to Key-Value Observing (KVO) and object deallocation.  Failure to remove KVO observers before the observed object is deallocated can lead to crashes or undefined behavior.

The `bug.m` file shows the problematic code where an observer is added but not always removed, creating the potential for a crash. The `bugSolution.m` file provides a corrected implementation which addresses this issue.

## How to Reproduce

1. Clone this repository.
2. Open the project in Xcode.
3. Run the application.  The buggy version will likely crash, while the corrected version will run without issue.

## Solution

The solution lies in ensuring that KVO observers are always removed using `removeObserver:forKeyPath:` before the observed object is deallocated. This should be done in the `dealloc` method or before the observer is no longer needed (e.g., when the view controller is dismissed).