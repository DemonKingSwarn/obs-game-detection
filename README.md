# obs-game-detection

A short script for OBS (Linux platform only) that seeks to add a "game detection" functionality enabling OBS replay buffer recordings to be automatically placed into sub-directories/folders based on the game being played when it is saved.

This is similar to the functionality of ShadowPlay instant replay recordings, although desired games must be added manually.

## Functionality 

- Replay buffer output files will be automatically moved after being saved to file.

    - If there is a detected game running (add games to `games.cfg`, see below), the buffer recording will be placed into the directory/folder for that game.

    - If there are no detected games running, the buffer recording will be placed in a directory using the current OBS scene name.

- This script will also start the replay buffer automatically when OBS launches. This functionality can be disabled by replacing a line near the top of the script `start_buffer_on_startup = True` with `start_buffer_on_startup = False`.

## Installation into OBS Studio

Tools -> Scripts

## Adding Games 

Adding games to be detected is done in the games.cfg file, and the format should be fairly self-explanatory, some examples are included in the file. Each game must be on a new line, and it is the PROCESS NAME (check for running games in task manager, do not include .exe in games.cfg). If you wish to specify a custom output folder name for a game, use a colon, as can be seen in the example entries in the file. If no name is provided, the process name will also be used as the folder name.

The custom folder name must be a valid Windows filename or the output will fail. Process names can be assumed to be valid Windows filenames.

The script must be reloaded (repeat icon in the OBS scripts UI, or restarting OBS will also accomplish this).

Non-aliased: The line Beat Saber being present in the games.cfg means that if Beat Saber.exe is running when the replay buffer is saved, that file will be moved to a Beat Saber sub-directory in your recording directory.

Aliased: The line r5apex: Apex Legends being present in the games.cfg means that if r5apex.exe is running when the replay buffer is saved, that file will be moved to an Apex Legends subdirectory in your recording directory.
