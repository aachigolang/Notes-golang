### scylladb config


in Scylla 3.1, mc format is enabled by default but In Scylla 3.0, mc format is disabled by default
enable_sstables_mc_format: true

#### Scylla configuration files are
/etc/default/scylla-server (Ubuntu/Debian) 
/etc/sysconfig/scylla-server (others)
/etc/scylla/scylla.yaml
/etc/scylla/cassandra-rackdc.properties


#### Address Configuration in Scylla