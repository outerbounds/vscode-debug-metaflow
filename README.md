# Debugging Metaflow with VSCode

> A minimal configuration & example debugging Metaflow Flows with VSCode.  

Because Metaflow launches python subprocesses to run Flows, debugging with `pdb` or `ipdb` is not straightforward.  However, VSCode provides utilities to make debugging these types of programs easy.

We enable debugging of Metaflow in VSCode by add the right configuration in your project's settings in [.vscode/launch.json](.vscode/launch.json).

Here is a recording of the end-to-end setup proccess:


https://user-images.githubusercontent.com/1483922/153103811-c40bf6bd-841c-4f63-b0fd-532e3949eb2f.mp4


You can now set breakpoints and then select "Start Debugging" from the "Debug" menu. Note that since Metaflow may launch multiple steps in parallel, you may actually hit multiple breakpoints at the same time; you will be able to switch between those breakpoints by selecting the proper function stack in the "Call Stack" window. You can also restrict Metaflow to only execute one step at a time by adding the values "--max-workers" and  "1" to the "args" array in the configuration.

### Combining debugging with resume

You can naturally combine the techniques described in this section with the "resume" command described previously. Instead of passing "run" as the program argument, simply pass "resume".

### Compatibility with Conda decorator

The above instructions work even if you use [`@conda` decorators](dependencies.md#managing-dependencies-with-conda-decorator) in your code; you need, however, to ensure that the `conda` binary is available in your `PATH`. The easiest way to do this is to set the `PATH` environment variable to properly include the path to the `conda` binary if it is in a non-standard location. In VSCode, you can simply add this value in the env section of launch.json and in PyCharm, the UI allows you to set environment variables.
