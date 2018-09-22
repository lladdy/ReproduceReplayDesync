# Reproduce replay desync issue (Only for Linux)
## Requirements
- An SC2 install with the map AcidPlantLE.SC2Map available (or just change the code to use a map that you have).
- CMake
- make
- A SC2 install on windows for verification 
## Steps
Clone, build and run this project.
```bash
# clone project
git clone --recursive https://github.com/lladdy/ReproduceReplayDesync.git

# build project
cd ReproduceReplayDesync
./build.sh

# run project
cd build/bin/
./ReproduceReplayDesync -e /path/to/SC2_x64
```
## Reproducing the issue
ReproduceReplayDesync will run a game each time it's executed and save 2 replays (one per SC2 instance) to the local directory.
The game will be between two DebugBots who will both issue random commands to their SCVs at first. After a while, one of the DebugBots will have their SCVs kill their own command centre.

It might take a number of runs before the program reproduces the issue.
On my machine it was commonly less than 10 tries, but never more than 20.

You will know you have produced the issue when you see at least one replay that is significantly larger in file size than the others.

Once a much larger replay file has been produced, move it over to a windows machine with SC2 installed and view it. You should observe that bot actions either cease part way through or are entirely missing.

## Additional notes
- I am yet to see a faulty replay produced after a machine restart (though it might simply be that I haven't tried enough times to trigger it).
- If you go to line 225 of reproducereplaydesync/main.cpp and comment out the 2 lines there and then recompile, you should find that the replay issue is no longer reproduced for whatever reason.