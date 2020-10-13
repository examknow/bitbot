# Writing your first module
Hello and welcome to BitBot! In this tutorial, you will learn to write your own module.
## Set up the file
First, let's create the file
> cd ~/bitbot/modules>

> touch sample.py>

Now, open the file with the editor of your choice (here we use nano)

> nano sample.py>

Next, we will add the dependencies needed to write the module

        #--depends-on commands
        from src import ModuleManager, utils

## Write the module
Now, the fun part! Let's write the module. This module will make the bot respond to the command `!doot` and will respond with `doot doot`.

To make the bot recognize the '!doot' command we need this line inside of our module's class:

        class Module(ModuleManager.BaseModule):
            @utils.hook("received.command.doot")

Now, let's add some help text:

        @utils.kwarg("help", "Makes the bot doot")

So, we have the command ready, but we don't make it do anything. Let's fix that.

        def doot(self, event):
            event["stdout"].write("doot doot")

And there we have it! Now we have a dooting bot.

## Full code

        #--depends-on commands
        from src import ModuleManager, utils
        class Module(ModuleManager.BaseModule):
            @utils.hook("received.command.doot")
            @utils.kwarg("help", "Makes the bot doot")
            def doot(self, event):
                event["stdout"].write("doot doot")
