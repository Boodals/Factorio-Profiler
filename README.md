# Factorio Profiler

A profiling tool for Factorio, by Boodals.

Usage:

`/startProfiler excludeCalledMs` (Command)

`Profiler.Start(excludeCalledMs)` (Script)

Starts the profiler. Any function called between the profiler starting and the profiler stopping will be recorded. If `excludeCalledMs` is given (not empty in the command version, or `true` in the script version), it will exclude the time it takes for subfunctions to be called. For example, if function A calls function B, and `excludeCalledMs` is true, the log will only show the time function A uses directly, not the time function B uses.

`/stopProfiler averageMs` (Command)

`Profiler.Stop(averageMs, message)` (Script)

Stops the profiler. After stopping, it will automatically dump the stored data into the console. If `averageMs` is given (not empty in the command version, or `true` in the script version), it will print the average time each function call takes as opposed to the total time. For example, if function A is called 10 times, each taking 0.5ms, the average time will be 0.5ms, whereas the total time will be 5ms.


Sample output: https://i.gyazo.com/81533760bc6499fb69b71d51bd3ebe0b.png

It is intentionally desync unsafe. Do not use it in multiplayer.

The profiler is super useful for finding the most expensive parts of scripts, but it does add a significent overhead to any function calls, so it should not be used for accurate performance metrics. If you want to accurately measure performance, you should use the LuaProfiler object from the Factorio API (game.create_profiler).
It is also useful for just knowing what functions are getting called, without having to put prints or logs in a bunch of functions, which are often forgotten and left in releases.

The log file is sorted in order of the number of times each function is called. There is no way to sort it by the time taken, unfortunately, otherwise I would have.

Have fun scripting. Feel free to improve on it, and send in pull requests if you think the changes are useful for everyone.
