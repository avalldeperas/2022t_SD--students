# Distributed Systems: First Practice (PR1)

## Time Stamped Anti-Entropy protocol

###Implementation and testing of Log and TimestampVector data structures

Phase 1 will consist of implementing the methods from `Log` and `TimestampVector` data structures.
In this phase only add operations are issued. Don't implement the functionality to purge the log.
Annex A includes details about the timestamps used in this practical assignment.

**NOTE:** be **careful with concurrent access to data structures.** Two actions issued by differentthreads may interleave. **Use** some **synchronization mechanism to avoid interference.**

Implement `Log` and `TimestampVector` data structures according to the TSAE protocol described in section *Time Stamped Anti-Entropy (TSAE) protocol.*

All scripts for running local tests are prepared for Ubuntu-linux but other OS can be used. In that case, you will be responsible for adapting the scripts to your OS.

### Test locally

To test locally Log and TimestampVector data structures run:

Run from scripts folder:
`$ java -cp ../bin:../lib/* recipes_service.Server --phase1`  (run from scripts folder)

Introduce a recipe and check if Log and TimestampVector data structures are correct


Then, run from scripts folder:
`$ ./start.sh 20004 --phase1`
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

| Subdirectory 	|	Content											|
| `/doc` 		|	Solution theoretical exercise.Report in pdf.	|
| `/src`		|	Log and TimestampVector classes. 				|