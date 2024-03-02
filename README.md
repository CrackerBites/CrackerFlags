# CrackerFlags & Optimization Guide
Fastflags, created by CrackerBites, aim to ensure maximum performance wherever possible!

These are the flags I've spent way too many hours creating, enduring lots of server crashes for no reason. Now, I'm publicly sharing them specifically for [Servcity](https://servcity.org/) customers.
> [!CAUTION]
> **I am not responsible for any negative impact on your server or data loss resulting from the use of these flags. By using these flags or applying my optimisations, you agree that all consequences are your own responsibility.**
>
> *I won't be explaining what each fastflag does. If you want to know, please do your own research.*

 **Supported server jars:**
- [x] Spigot and all of its forks!

*This applies to the GraalVM Fastflags and OpenJ9. The Etil flags should work fine regardless of what you are using. As for OpenJ9 and GraalVM, everything else is untested and likely won't be, as I don't see any reason to run modded servers.*

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
> [!NOTE]
> I recommend removing the following `--modules=jdk.incubator.vector` if you dont use a fork of pufferfish or pufferfish itself otherwise its useless having it there and also `-DIReallyKnowWhatIAmDoingISwear` this is an spigot only flag remove it if you want to get notified if you are using an old build this skips the checks for a faster startup this also applies for [Graalvm](https://github.com/CrackerBites/CrackerFlags/blob/main/README.md#these-fastflags-downbelow-are-specifically-made-for-graalvm-this-is-what-i-personally-use-and-what-will-probably-get-updated-the-most).
### Fastflags for any other java version downbelow.
> [!IMPORTANT]
> These Fastflags below are Etil flags. I recommend these over Aikar flags, which are slightly modified by me. There isn't much to improve on they use the G1GC garbage collector. Some people swear by Shenandoah GC or ZGC, but in my own research, they perform better on the client than on the server, and they have more drawbacks, only beneficial for zero or less pauses.

**These downbelow are recommended for higher less than 12 gig allocated RAM.**
```java
java -Xms128M -XX:MaxRAMPercentage=95.0 -XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurvivorRatio=32 -XX:+PerfDisableSharedMem -XX:MaxTenuringThreshold=1 -XX:-UseBiasedLocking -XX:UseAVX=3 -XX:+UseStringDeduplication -XX:+UseFastUnorderedTimeStamps -XX:+UseAES -XX:+UseAESIntrinsics -XX:UseSSE=4 -XX:+UseFMA -XX:AllocatePrefetchStyle=1 -XX:+UseLoopPredicate -XX:+RangeCheckElimination -XX:+EliminateLocks -XX:+DoEscapeAnalysis -XX:+UseCodeCacheFlushing -XX:+SegmentedCodeCache -XX:+UseFastJNIAccessors -XX:+OptimizeStringConcat -XX:+UseCompressedOops -XX:+UseThreadPriorities -XX:+OmitStackTraceInFastThrow -XX:+TrustFinalNonStaticFields -XX:ThreadPriorityPolicy=1 -XX:+UseInlineCaches -XX:+RewriteBytecodes -XX:+RewriteFrequentPairs -XX:+UseNUMA -XX:-DontCompileHugeMethods -XX:+UseFPUForSpilling -XX:+UseFastStosb -XX:+UseNewLongLShift -XX:+UseVectorCmov -XX:+UseXMMForArrayCopy -XX:+UseXmmI2D -XX:+UseXmmI2F -XX:+UseXmmLoadAndClearUpper -XX:+UseXmmRegToRegMoveAll -Dfile.encoding=UTF-8 -Xlog:async -Djava.security.egd=file:/dev/urandom -DIReallyKnowWhatIAmDoingISwear --add-modules jdk.incubator.vector -jar server.jar nogui
```
**These downbelow are recommended for higher than 12 gig allocated RAM.**
```java
java -Xms128M -XX:MaxRAMPercentage=95.0 -XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions -XX:+UnlockDiagnosticVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=40 -XX:G1MaxNewSizePercent=50 -XX:G1HeapRegionSize=16M -XX:G1ReservePercent=15 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=20 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurvivorRatio=32 -XX:+PerfDisableSharedMem -XX:MaxTenuringThreshold=1 -XX:-UseBiasedLocking -XX:UseAVX=3 -XX:+UseStringDeduplication -XX:+UseFastUnorderedTimeStamps -XX:+UseAES -XX:+UseAESIntrinsics -XX:UseSSE=4 -XX:+UseFMA -XX:AllocatePrefetchStyle=1 -XX:+UseLoopPredicate -XX:+RangeCheckElimination -XX:+EliminateLocks -XX:+DoEscapeAnalysis -XX:+UseCodeCacheFlushing -XX:+SegmentedCodeCache -XX:+UseFastJNIAccessors -XX:+OptimizeStringConcat -XX:+UseCompressedOops -XX:+UseThreadPriorities -XX:+OmitStackTraceInFastThrow -XX:+TrustFinalNonStaticFields -XX:ThreadPriorityPolicy=1 -XX:+UseInlineCaches -XX:+RewriteBytecodes -XX:+RewriteFrequentPairs -XX:+UseNUMA -XX:-DontCompileHugeMethods -XX:+UseFPUForSpilling -XX:+UseFastStosb -XX:+UseNewLongLShift -XX:+UseVectorCmov -XX:+UseXMMForArrayCopy -XX:+UseXmmI2D -XX:+UseXmmI2F -XX:+UseXmmLoadAndClearUpper -XX:+UseXmmRegToRegMoveAll -Dfile.encoding=UTF-8 -Xlog:async -Djava.security.egd=file:/dev/urandom -DIReallyKnowWhatIAmDoingISwear --add-modules jdk.incubator.vector -jar server.jar nogui
```
> [!NOTE]
> I recommend removing the following `--modules=jdk.incubator.vector` if you dont use a fork of pufferfish or pufferfish itself otherwise its useless having it there and also `-DIReallyKnowWhatIAmDoingISwear` this is an spigot only flag remove it if you want to get notified if you are using an old build this skips the checks for a faster startup this is the same for the previous flags.

# Optimization Guide
> [!CAUTION]
> **THIS IS AN WIP = WORK IN PROGRESS**
## Server softwares
**I personally recommend the following:**
- [Purpur](https://purpurmc.org/)
- [Leaf](https://github.com/Winds-Studio/Leaf)
- [Pufferfish](https://github.com/pufferfish-gg/Pufferfish)

*i use Leaf myself personally as its the most optimised of the bunch.*
> [!IMPORTANT]
> Do not use spigot or bukkit i even recommend staying away from paper because purpur and pufferfish are way better alternatives with the same functionality or even more especially in purpur's case.

### Config settings

#### server.properties

**View distance:**
`Recommended value: 7`

*this doesnt matter when ur chunks are preloaded by chunky or any other plugin then just put it on whatever you want and also this changes allot of the gameplay and could annoy your players so choose wisely otherwise stick with 12.*
![](https://github.com/CrackerBites/CrackerFlags/blob/main/Preview%201.gif)

**Simulation distance:**
`Recommended value: 4`

*i recommend having this usually being half ur render distance*
![](https://github.com/CrackerBites/CrackerFlags/blob/main/Preview%202.0.gif)

#### Bukkit.yml

**ticks-per:**
Recommended value: 
```java
- animals: 16
- monsters: 24
- misc: 8
- water: 8
- villagers: 16
- flying-monsters: 48
```
