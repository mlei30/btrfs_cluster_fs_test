# btrfs_testbed
Use btrfs as a base to develop cluster file system.

There are a few recent cluster file systems such as ceph, gfs/hadoop, even amazon S3 object storage. They use either a central meta data server (A) or fixed distributed formula (B). A suffers performance bottleneck/poor scale. B suffers hotspot and has ifficult to mitigate the data. There is also panzura globlal file system (C) using global file locking which pretty the traditional way to implement cluster file system with shared storage. But locking may limit the scale and the implementation may be tricky. I am not aware of other approaches to implement cluster file system.

I want to design a cluster file system that can be used inside data center or across geographic locations (either data centers or branch offices at different locations), without global locks. The readers/writers should implement on top of file system which is quite similar to GIT principle. Other ideas of mine has something to do with transactional memory, storage routing, data shipment.

Therefore to use btrfs as baseline to build experiment vehicle for all these ideas is to shrink btrfs to basic and then hook with fuse to make it usable as the first milestone.

