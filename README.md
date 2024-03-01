# CrackerFlags
Fastflags, created by CrackerBites, aim to ensure maximum performance wherever possible!

These are the flags I've spent way too many hours creating, enduring lots of server crashes for no reason. Now, I'm publicly sharing them specifically for [Servcity](https://servcity.org/) customers.
> [!CAUTION]
> **I am not responsible for any negative impact on your server or data loss resulting from the use of these flags. By using these flags, you agree that all consequences are your own responsibility.**
>
> *I won't be explaining what each fastflag does. If you want to know, please do your own research.*

 **Supported server jars:**
- [x] Spigot and all of its forks!

*Everything else is untested and likely won't be, as I don't see any reason to run modded servers.*

### These Fastflags downbelow are specifically made for [Graalvm](https://www.graalvm.org/downloads/#) this is what i personally use and what will probably get updated the most.
> [!IMPORTANT]
> Keep in mind that these flags are specifically designed for Java 21, not 17. You may experience a loss in performance if used with Java 17 instead.
>
> These are recommended for server that have 4+ gigs allocated RAM otherwise i recommend [OpenJ9](https://github.com/CrackerBites/CrackerFlags?tab=readme-ov-file#these-fastflags-downbelow-are-specifically-made-for-openj9) below!
```java
java -Xms128M -XX:MaxRAMPercentage=95.0 -XX:+UseG1GC -XX:MaxGCPauseMillis=130 -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:+ParallelRefProcEnabled -XX:G1NewSizePercent=28 -XX:G1HeapRegionSize=16M -XX:G1ReservePercent=20 -XX:G1MixedGCCountTarget=3 -XX:InitiatingHeapOccupancyPercent=10 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:SurvivorRatio=32 -XX:MaxTenuringThreshold=1 -XX:+PerfDisableSharedMem -XX:G1SATBBufferEnqueueingThresholdPercent=30 -XX:G1ConcMarkStepDurationMillis=5 -XX:G1RSetUpdatingPauseTimePercent=0 -XX:+UseNUMA -XX:-DontCompileHugeMethods -XX:MaxNodeLimit=240000 -XX:NodeLimitFudgeFactor=8000 -XX:ReservedCodeCacheSize=400M -XX:NonNMethodCodeHeapSize=12M -XX:ProfiledCodeHeapSize=194M -XX:NonProfiledCodeHeapSize=194M -XX:NmethodSweepActivity=1 -XX:+UseCriticalJavaThreadPriority -XX:AllocatePrefetchStyle=3 -XX:+UseTransparentHugePages -XX:LargePageSizeInBytes=2M -XX:+UseLargePages -XX:+EagerJVMCI -XX:+UseFastUnorderedTimeStamps --add-modules=jdk.incubator.vector -DIReallyKnowWhatIAmDoingISwear -jar server.jar --nogui
```
### These Fastflags downbelow are specifically made for [Openj9](https://github.com/eclipse-openj9/openj9).
> [!CAUTION]
> OpenJ9 behaves weird, so I don't recommend it for big servers with lots of plugins. Instead, try using GraalVM it's faster and more reliable. OpenJ9 is slow compared to GraalVM and its alternatives. So i only suggest using OpenJ9 for servers with very high RAM usage or survival servers with less than 4 gigs of allocated RAM. In my experience, OpenJ9 can have many incompatibilities, especially with plugins like [LPX](https://builtbybit.com/resources/lpx-antipacketexploit.15709/) and [no-chat-report](https://modrinth.com/mod/no-chat-reports/versions) I used OpenJ9 as my main Java for a while until I switched to GraalVM because of these incompatibilities.
```java
java -Xms128M -XX:MaxRAMPercentage=95.0 -XX:+IdleTuningGcOnIdle -XX:+UseAggressiveHeapShrink -XX:-OmitStackTraceInFastThrow -XX:+UseFastAccessorMethods -Xshareclasses:allowClasspaths -XX:+AlwaysPreTouch -XX:+ClassRelationshipVerifier -Xshareclasses:cacheDir=./cache -Xaot -XX:+UseCompressedOops -XX:ObjectAlignmentInBytes=256 -Xshareclasses -XX:SharedCacheHardLimit=800M -Xscmx800M -Xtune:virtualized -XX:InitialTenuringThreshold=5 -Dlog4j2.formatMsgNoLookups=true -XX:-DisableExplicitGC -XX:+UnlockExperimentalVMOptions -XX:MaxGCPauseMillis=6 -Djava.net.preferIPv4Stack=true -XX:-ParallelRefProcEnabled -XX:+UseTLAB -Xmn200M -Xmx1G -Xms201M -XX:ParallelGCThreads=2 -XX:ConcGCThreads=1 -DIReallyKnowWhatIAmDoingISwear --add-modules=jdk.incubator.vector -jar server.jar --nogui
```
### Fastflags for any other java version downbelow.
> [!NOTE]
> There will be coming Fastflags for java openjdk improved on aikar and etil flags i dont know when and there is no confirmed date because i dont use this myself!
