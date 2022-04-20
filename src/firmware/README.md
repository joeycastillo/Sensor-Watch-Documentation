Sensor Watch Firmware
=====================

While you can build any number of bare-metal applications for Sensor Watch, when we refer to the Sensor Watch firmware, we're really talking about _Movement_, the community firmware for Sensor Watch. You can read more about Movement [here](); for now, the important thing to know is that it manages a series of _watch faces_ that you advance through using the _mode_ button. It's a very similar idiom to the classic Casio F-91W, which advances from `Clock -> Alarm -> Stopwatch -> Time Set`, and then wraps around to `Clock`.

The stock build of Movement offers many more watch faces — some of which, like World Clock, you can include more than once! Still: you'd be pressing the Mode button for hours if we included them all, so instead, we only build a subset of the available faces into any given firmware. This means that you can [build a custom firmware]() download an anternate firmware that includes the kind of functionality you want, or build a custom firmware that includes just the watch faces you desire.

This chapter is broken up into three sections, but I recommend you start here: [Download prebuilt firmware for Sensor Watch](prebuilt.md). If the prebuilt firmware options don't suit you, you can move on to [building custom firmware for Sensor Watch](building.md). Finally, if you want to try out different options without taking your watch apart again and again, you can also [build custom firmware for the Sensor Watch Emulator](emulator.md).
