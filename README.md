# Silent Data Loss in Core Data (Objective-C)

This repository demonstrates a common, yet easily missed, bug in Objective-C Core Data applications.  The bug involves silent data loss due to a failure to explicitly save changes to the `NSManagedObjectContext`.  The example shows how to reproduce the error and how to correct it.

## Reproducing the Bug

The `BuggyCoreData.m` file contains code that creates a new managed object, modifies it, and then *fails* to save the changes to the persistent store.  Running this code will not result in any errors, but the data changes will not be saved.

## Solution

The `FixedCoreData.m` file demonstrates the correct approach.  It explicitly saves the changes to the context using `[context save:&error];`  This ensures data persistence.

## How to Use

1. Clone this repository.
2. Open the Xcode project.
3. Run the `BuggyCoreData` target to observe the bug in action.
4. Run the `FixedCoreData` target to see the corrected version.

This example highlights the importance of meticulous memory management and error handling in Core Data development.