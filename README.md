# Distributed Systems: First Practice (PR1)

## Time Stamped Anti-Entropy protocol

### Implementation and testing of Log and TimestampVector data structures

Phase 1 will consist of implementing the methods from `Log` and `TimestampVector` data structures.
In this phase only add operations are issued. Don't implement the functionality to purge the log.
Annex A includes details about the timestamps used in this practical assignment.

**NOTE:** be **careful with concurrent access to data structures.** Two actions issued by differentthreads may interleave. **Use** some **synchronization mechanism to avoid interference.**

Implement `Log` and `TimestampVector` data structures according to the TSAE protocol described in section *Time Stamped Anti-Entropy (TSAE) protocol.*

All scripts for running local tests are prepared for Ubuntu-linux but other OS can be used. In that case, you will be responsible for adapting the scripts to your OS.



### Test locally

To test locally Log and TimestampVector data structures run:

Run from scripts folder:

```
$ java -cp ../bin:../lib/* recipes_service.Server --phase1
``` 

Introduce a recipe and check if Log and TimestampVector data structures are correct

Then, run from scripts folder:

```
$ ./start.sh 20004 --phase1
```

$1: listening port of `Phase1TestServer`, the server that tests the correctness of your solution. In case that port 20004 is already in use by another application you can change it to any other unused port.

The above script executes `Log` and `TimestampVector` with a predefined set of users and operations and compares it with a `Log` and `TimestampVector` previously calculated.



### Things to deliver

A **file** according to the following convention:
<center>**Deliverable1-Year-FamilyName1_Name1.zip**</center>

This file should **include**:

- solution of the theoretical exercise.

- phase1.pdf: a (short) report detailing and explaining all decisions taken. A proposal of report template is included in the practical assignment distribution (`/doc` folder). In addition, you should detail the portions of your source code you consider are most significant.

- Source code: `Log` and `TimestampVector` classes. 

The zip file should have a single directory named like the zip file with the following structure (use same structure and names):

| Subdirectory 	|	Content											                  |
|---------------|-----------------------------------------------|
| `/doc` 		    |	Solution theoretical exercise.Report in pdf.	|
| `/src`		    |	Log and TimestampVector classes. 				      |


--------------------------------------------------------------------------------------------

**Important:** do not implement new classes. Modify only the classes indicated in each phase.

Classes that you should modify:

1. package `recipes_service.tsae.datastructures`:
	- `Log`: class that logs operations.
	- `TimestampVector`: class to maintain the summary.
	- `TimestampMatrix`: class to maintain the acknowledgment matrix of timestamps
	
2. package `recipes_service.tsae.sessions`:
  - `TSAESessionOriginatorSide`: Originator protocol for TSAE.
	- `TSAESessionPartnerSide`: Partner's protocol for TSAE.

3. package `recipes_service`:
  - `ServerData`: contains Server's data structures required by the TSAE protocol (log, summary, ack) and the application (recipes). You can add any required method to allow `TSAESessionOriginatorSide` and `TSAESessionPartnerSide` to manipulate these data structures.
    - addRecipe method: adds a new recipe.
    - removeRecipe method: removes a recipe.

**Classes that you should use but NOT modify:**

4. package recipes_service.tsae.data_structures:
  - `Timestamp`: a timestamp. A timestamp allows the ordering of operations issued from the same host. It is a tuple <hostId, sequenceNumber>. Sequence number is a number that grows monotonically. The first valid timestamp issued by a host will have an initial value of 0. A negative sequence number means that the host hasn't issued yet any operation. Timestamps can not be used to order operations issued in different hosts. Next timestamp is obtained by calling the method `nextTimestamp()` from class `ServerData` (package `recipes_service`).
  
5 package recipes_service.data:
  - `AddOperation`: an add operation (operations are logged in the `Log` and exchanged with other partners).
  - `RemoveOperation`: a remove operation (operations are logged in the `Log` and exchanged with other partners).
  - `Recipe`: a recipe.
  - `Recipes`: class that contains all recipes.

