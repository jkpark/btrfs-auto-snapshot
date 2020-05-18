# btrfs-auto-snapshot

Take snapshot(if there is change) and retains snapshots.
> not detect all types of changes, for example: deleted files.

### Structure of btrfs should be

```
 /mnt/hdd1                                                (volume root directory)
   +-- @workspace                                         (subvolume root directory)
   \-- snapshots                                          (directory)
       \-- workspace                                      (directory)
           +-- @workspace_autosaved_2020.04.22_12.23.44   (snapshot of subvolume "@workspace")
           +-- @workspace_autosaved_2020.04.22_12.26.29   (snapshot of subvolume "@workspace")
           +-- workspace_autosaved_latest                 (symbolic link of latest snapshot of "@workspace")
```

### Usage
Schedule to run `btrfs-autosnap` with cron

```
*/15 *  * * *   root    /usr/local/etc/btrfs-autosnap -c 8 workspace
```

`-c` option is retainning count
