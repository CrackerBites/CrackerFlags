# CrackerFlags
Fastflags made by CrackerBites ensuring max performance wherever its possible!

These are the flags i spent countless hours on creating or enduring lots of server crashes for no reason and now im publicly sharing them specifically for [Servcity](https://servcity.org/) customers.
> [!CAUTION]
> **I am not held responsible for anything that would impact your server in an negative way or even dataloss in general when you use these flags you agree that its all on your own responsibilty!**
>
> *I wont be explaining what each fastflag does if you want to know do your own research.*

 **Supported server jars:**
- [x] Spigot and all of its forks!

*everything else is not tested and probably wont as i dont see any reason to run modded servers.*

### These Fastflags downbelow are specifically made for [Graalvm](https://www.graalvm.org/downloads/#) this is what i personally use and what will probably get updated the most.
> [!IMPORTANT]
> Keep in mind these flags are specifically made for java 21 not 17! You will lose on performance using it on 17 instead.
>
> These are recommended for server that have 4+ gigs allocated ram otherwise i recommend openj9 below!
```java
java -Xms128M -XX:MaxRAMPercentage=95.0 -XX:+UseG1GC -XX:MaxGCPauseMillis=130 -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:+ParallelRefProcEnabled -XX:G1NewSizePercent=28 -XX:G1HeapRegionSize=16M -XX:G1ReservePercent=20 -XX:G1MixedGCCountTarget=3 -XX:InitiatingHeapOccupancyPercent=10 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:SurvivorRatio=32 -XX:MaxTenuringThreshold=1 -XX:+PerfDisableSharedMem -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:+UseNUMA -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:NmethodSweepActivity=1 -XX:+UseCriticalJavaThreadPriority -XX:AllocatePrefetchStyle=3 -XX:+UseTransparentHugePages -XX:LargePageSizeInBytes=2M -XX:+UseLargePages -XX:+EagerJVMCI -XX:+UseFastUnorderedTimeStamps --add-modules=jdk.incubator.vector -DIReallyKnowWhatIAmDoingISwear -jar server.jar --nogui
```
### These Fastflags downbelow are specifically made for [Openj9](https://github.com/eclipse-openj9/openj9).
> [!CAUTION]
> Openj9 is very weird behaving i do not recommend it for big servers with lots of plugins try using graalvm instead and another thing worth noting it is very slow compared to graalvm and its alternatives i only recommend Openj9 to servers with way too high ram usage or survival servers that are under 4 gig of ram allocated openj9 could have lots of incompatibilities in my own testing and experience as i have used this as my main java for a while till i switched over to graalvm because of incompatibilties its known to struggle with plugins like [LPX](https://builtbybit.com/resources/lpx-antipacketexploit.15709/) and [no-chat-report](https://modrinth.com/mod/no-chat-reports/versions).
```java
java -Xms128M -XX:MaxRAMPercentage=95.0 -XX:+IdleTuningGcOnIdle -XX:+UseAggressiveHeapShrink -XX:-OmitStackTraceInFastThrow -XX:+UseFastAccessorMethods -Xshareclasses:allowClasspaths -XX:+AlwaysPreTouch -XX:+ClassRelationshipVerifier -Xshareclasses:cacheDir=./cache -Xaot -XX:+UseCompressedOops -XX:ObjectAlignmentInBytes=256 -Xshareclasses -XX:SharedCacheHardLimit=800M -Xscmx800M -Xtune:virtualized -XX:InitialTenuringThreshold=5 -Dlog4j2.formatMsgNoLookups=true -XX:-DisableExplicitGC -XX:+UnlockExperimentalVMOptions -XX:MaxGCPauseMillis=6 -Djava.net.preferIPv4Stack=true -XX:-ParallelRefProcEnabled -XX:+UseTLAB -Xmn200M -Xmx1G -Xms201M -XX:ParallelGCThreads=2 -XX:ConcGCThreads=1 -DIReallyKnowWhatIAmDoingISwear --add-modules=jdk.incubator.vector -jar server.jar --nogui
```
### Fastflags for any other java version downbelow.
> [!NOTE]
> There will be coming Fastflags for java openjdk improved on aikar and etil flags i dont know when and there is no confirmed date because i dont use this myself!
