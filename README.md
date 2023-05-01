Download Link: https://assignmentchef.com/product/solved-embsys105-assignment-4-task-synchronization-with-ucos
<br>
This assignment exercises most task synchronization services provided by uCOS, namely semaphores, mailboxes, queues, and event flags. Services such as these are commonly provided by kernels and it will be useful to become familiar with them in preparation for developing event driven applications.

<ol>

 <li>Download and unzip the taskSync project contained in the zip file: taskSync.zip</li>

 <li>Open the taskSync.eww workspace in the EWARM IDE.</li>

 <li>Make sure the taskSync project builds. There will be a dozen or so warnings which will go away after you add missing code.</li>

 <li>Launch TeraTerm</li>

 <li>Build and upload the project and start it running.</li>

 <li>It will not run very far until you substitute your uCOS port code from Assignment 3 into os_cpu_a.asm.</li>

 <li>After adding your port code, run the app and you should see a jumble of status messages in the UART from the various tasks.</li>

 <li>Your job is to add missing code to sort out the status messages so they don’t interrupt each other and ensure that any reported errors are fixed.</li>

</ol>

The application consists of 7 tasks not including the uCOS startup task:

<strong>Mailbox related tasks:</strong>

<ol>

 <li>TaskMBTx is a task that uses mailboxes to transmit messages to two other tasks, TaskMBRxA and TaskMBRxB.</li>

 <li>TaskMBRxA is a task that receives messages from TaskMBTx.</li>

 <li>TaskMBRxB is another task that receives messages from TaskMBTx.</li>

</ol>

<strong>Queue related tasks:</strong>

<ol start="4">

 <li>TaskQTxA is a task that uses a message queue to transmit messages to TaskQRx.</li>

 <li>TaskQTxB, like TaskQTxA, also uses the message queue to transmit message to TaskQRx.</li>

 <li>TaskQRx is a task that receives messages from TaskQTxA and TaskQTxB using a message queue.</li>

</ol>

<strong>Event flag related task:</strong>

<ol start="7">

 <li>TaskRxFlags is a task that helps synchronize the two mailbox related receiver tasks, TaskMBRxA and TaskMBRxB so that they wait for each other to finish receiving one message before either one is permitted to receive the next message.</li>

</ol>

<strong>What to Code:</strong>

Do a global search in the project for the string “TODO”. This will find all the places you need to add code. Here is the suggested order for completing the assignment:

<ol>

 <li>Follow the “TODO semPrint” instructions in the code to use a binary semaphore, i.e. the initial counter value is 1, to protect critical code so delays and interrupts don’t mix up the output from different tasks.</li>

 <li>Follow the “TODO Mailbox” instructions in the code to send messages from TaskMBTx to TaskMBRxA and TaskMBRxB using uCOS mailboxes.</li>

 <li>Follow the “TODO Queue” instructions in the code to send messages from TaskQTxA and TaskQTxB to TaskQRx using a uCOS queue.</li>

 <li>Follow the “TODO EventFlags” instructions in the code to synchronize TaskMBRxA and TaskMBRxB using uCOS event flags so that neither one will attempt to receive their next message until both have received their current message.</li>

 <li>You should get a “Done!” message from each task and all “expected” and “actual” results should match.</li>

</ol>

<strong>Hint</strong>

Comment out calls to OSTaskCreate() for tasks you are not currently focusing on.