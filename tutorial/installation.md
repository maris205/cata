# Installation

## Getting Minerva

You could build Minerva from code source. It may take you several hours. So we recommend you install the minerva by release code.&#x20;

You could get releases of Minerva by wget:&#x20;

```
$ wget https://cata.oss-cn-hongkong.aliyuncs.com/src/apache-drill-1.16.0.zip
```

{% hint style="info" %}
&#x20;The file size is about 400M, it may take you 10-30 mins to download it.
{% endhint %}

Once you download the file, you could unzip the files:

```
unzip apache-drill-1.16.0.zip
```

Then you could install the run the Minerva as follows:

```
#step 0, install java
yum install java-1.8.0-openjdk  java-1.8.0-openjdk-devel -y
yum install tmux -y
#revise  apache-drill-1.16.0/conf/drill-env.sh, DRILL_HOST_NAME to your machine ip

#step 1, add service 
wget https://cata.oss-cn-hongkong.aliyuncs.com/src/drill-embedded.service
#please revise the path in drill-embedded.service

cp drill-embedded.service /usr/lib/systemd/system/

#step 2, add start
systemctl enable drill-embedded.service

#step 3, start
systemctl start drill-embedded.service

#visit http://ip:8047/
```

## Getting IPFS

Now CATA supports ipfs 0.7 version:

You could get the release：

```
wget https://cata.oss-cn-hongkong.aliyuncs.com/src/go_ipfs_0.4.23.tar.gz
```

&#x20;the tar the file as follows:

```bash
tar -xzvf go_ipfs_0.4.23.tar.gz
#install
cd go-ipfs
./install.sh
```

After install the ipfs, you could start the ipfs as follows:

```bash
#step 0, init ipfs
ipfs init
wget https://cata.oss-cn-hongkong.aliyuncs.com/src/swarm.key
cp swarm.key ~/.ipfs/

#step 1, add service 
wget https://cata.oss-cn-hongkong.aliyuncs.com/src/ipfsd.service 
cp ipfsd.service /usr/lib/systemd/system/

#step 2, add start
systemctl enable ipfsd.service

#step 3, start
systemctl start ipfsd.service
```

## Check installation

After install Minerva and ipfs, you could visit http://your-machine-ip:8047/

You should find the web page like this:

![](<../.gitbook/assets/image (17).png>)

Then click the "Storage" in top nav tab, you should find the ipfs plugin:

![](<../.gitbook/assets/image (5).png>)

if "ipfs" is not in left panel, please enable it.

Then you could add some files to ipfs and search them by SQL from Minerva.

First, you need download a python script and a test file:

```bash
wget https://cata.oss-cn-hongkong.aliyuncs.com/src/splitter.py
wget https://cata.oss-cn-hongkong.aliyuncs.com/src/test.json
```

The test.json is the metadata of some books. One line one data:

> {"id": "53e9a743b7602d9703079a7f", "title": "On the characteristics of a system having master and helping unit", "authors":  "S.K. Singh",...}
>
> {"id": "53e9a743b7602d9703079a80", "title": "Study on Zoning Nature of the Structural Deformation in Overlying Strata of Deep Mines","authors":"aaaa",....}

Then could add test.json by splitter.py:(If we use "ipfs add", this command my split one json data into 2 segments )

![](<../.gitbook/assets/image (3).png>)

Then, you could run sql for test.json in minerva web pages:

> select \* from ipfs.`/ipfs/Qmc7NGW5VQeTUSEfs88Ssj1S4xKZP6cjTqXgDKmrAoPrCa#json` limit 10

![](<../.gitbook/assets/image (12).png>)

You should get the result like this:

![](<../.gitbook/assets/image (8).png>)

Con! You finish the installation of 2 basic components of CATA.

