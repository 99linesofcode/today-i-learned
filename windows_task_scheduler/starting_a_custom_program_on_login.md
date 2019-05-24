# Starting a custom program on login

If you want a program to start up under Windows 10 and it does not have a corresponding service or requires admin privileges you may make use of the build in Task Scheduler. Open up the Task Scheduler and follow the steps below:

1. From the left sidebar highlight `Task Scheduler Library`. This reveals some actions in the sidebar on the right;
1. Click `Create Basic Task`. A modal is displayed;
1. Enter a name and, if you would like a description of the task you are about to add. Click `Next`;
1. Select `When I log on` and click `Next`;
1. Select `Start a program`. `Next`;
1. Browse to the location of the executable and click `Next`;
1. At this final step, check the checkbox `Open the Properties dialog for this task when I click Finish`.
1. On the `General` tab check `Run with highest privileges`;
1. On the `Conditions` tab uncheck all checkboxes;
1. On the `Settings` tab only check `Allow task to be run on demand` and press OK.
