# Password-Checker-Hadoop

## Basic Logic:

-In our master machine (process id 0) we will read shadow.txt file and use tokenize function to parse the sentence to get salt and encrypted key

-Then we send the length of salt, length of key, salt and encrypted key to each of the slave processes to use to search for password.

-We will dynamically divide passwords among the slaves based on password lengths e.g passwords of length 1-2 will go to one process, 3-4 will go to another and so on

-In case of 8(max length) not being divisible by number of processes the remainder will be taken up by the master itself to search.

-To search a function runs which tests all possible combinations of alph for its allotted length and returns true or false if password found or not.

-If password is found, the slave calls MPI_Abort to stop all other processes from continuing their search.

### NOTE:

We tested out code using 4 VMs, 3 slaves and 1 Master however it works best with 1 slave since our laptops do not have enough power to bear so many VMs and become unbearably slow.
