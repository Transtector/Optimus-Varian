Optimus-Varian Configuration Files
==============

These files describe a particular configuration used for the Cme to 
monitor a Power Conditioner for Varian Medical Systems.


The 3-phase output (LOAD) of the power conditioner isolation transformer
is monitored for voltage (Vrms) and current (Arms). The power conditioner
output is arranged in a WYE configuration, and the monitoring points are
assumed to be connected between the phases and neutral (L-N).  Monitoring
for this arrangement is configured using `ch0_config.json`,
`ch1_config.json`, and `ch2_config.json`.  An additional virtual channel
is configured with `ch3_config.json` that calculates the LOAD phase imbalance.  

The 3-phase input (LINE) of the power conditioner isolation transformer
is monitored for voltage (Vrms).  The power conditioner input is arranged in
a DELTA configuration, and the monitoring points are assumed to be connected
between each phase (L-L).  Monitoring for this arrangment is configured using
`ch4_config.json`, `ch5_config.json`, and `ch6_config.json`.  Additionally,
the LINE phase imbalance is calculated from a virtual channel defined
in `ch7_config.json`.


## Device Deployment

### Option 1: GitLab or GitHub

To get this configuration onto a Cme device that can perform the monitoring,
simply clone the project repository to the `/data/channels/` directory on the device.


```bash
root@cme[~:501] $ cd /data
root@cme[/data:502] $ git clone git@10.252.64.224:Cme-config/Optimus-Varian.git
root@cme[/data:503] $ mv Optimus-Varian/ channels/
```

### Option 2: Amazon AWS S3 Bucket

An archive of the latest configuration files is available on AWS.  Note that you
may need to create the `/data/channels/` directory first (as shown below), otherwise
just untar the package into the existing folder over the top of any configuration
files already in that location.

```bash
root@cme[~:501] $ cd /data
root@cme[/data:502] $ mkdir -p channels
root@cmd[/data:503] $ cd channels
root@cmd[/data/channels:504] $ curl -s https://s3.amazonaws.com/transtectorpublicdownloads/Cme/cme-config-varian.tgz | tar -xvz
```



