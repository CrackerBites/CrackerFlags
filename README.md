# CrackerFlags
Fastflags made by CrackerBites ensuring max performance where its possible.

These are the flags i spent countless hours on creating or enduring lots of server crashes for no reason and now im publicly sharing them specifically for [Servcity](https://servcity.org/) customers.
> [!CAUTION]
> **I am not responsible for anything that would impact your server in an negative way or even dataloss in general when you use these flags you agree that its all on your own responsibilty!**

These are Graalvm Fastflags
```json
{
java -Xms128M -XX:MaxRAMPercentage=95.0 -XX:+UseG1GC -XX:MaxGCPauseMillis=130 -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:+ParallelRefProcEnabled -XX:G1NewSizePercent=28 -XX:G1HeapRegionSize=16M -XX:G1ReservePercent=20 -XX:G1MixedGCCountTarget=3 -XX:InitiatingHeapOccupancyPercent=10 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:SurvivorRatio=32 -XX:MaxTenuringThreshold=1 -XX:+PerfDisableSharedMem -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:+UseNUMA -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:NmethodSweepActivity=1 -XX:+UseCriticalJavaThreadPriority -XX:AllocatePrefetchStyle=3 -XX:+UseTransparentHugePages -XX:LargePageSizeInBytes=2M -XX:+UseLargePages -XX:+EagerJVMCI -XX:+UseFastUnorderedTimeStamps --add-modules=jdk.incubator.vector -DIReallyKnowWhatIAmDoingISwear -jar server.jar --nogui }
```
