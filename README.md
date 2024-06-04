# harvester-certification

## Training Notes

### Harvester Deployment Process
The first 3 cluster nodes will act as the controller nodes for the cluster and run process such as **etcd** and the **Kubernetes API**. Any additional nodes will just be workers.


### Demonstration: Create a Harvester cluster
The default user to accesss Harvester nodes using SSH is Rancher. The user password is defined during the installation process.

### Automated Harvester Deployment
+ Automation can be done using network/iPXE installation method.
+ 2 files are used to automate the installation and the format is YAML.
+ The YAML can fully automate the deployment or provide additional configuration during a manual install

![alt text](image.png)

### Configure iPXE to Deploy Harvester
Install iPXE files/boot images in a management workstation.
Images available in the ipxe-bootimgs '''rpm -ql ipxe-bootimgs'''  This command shows all files inside the package.

We need to grab some images and put them into a directory that should be accessible thorugh the web because iPXE uses HTTP booting protocol. The files should go to a webroot or directory insed the webroot that will have all the iPXE things.
In the video they are using RMT that is running inside the management VM. Webroot = RMT server

The directory that will store all files is /var/lib/rmt/public/repo/Install/ipxe

The standard path from RMT is '''/var/lib/rmt/public'''
Then the instructor created more directories to store the ipxe files '''/repo/Install/ipxe'''

Inside that directory we will have 4 files.
+ 2 images (ipxe-x86_64.efi and undionly.kpxe)
+ two configuration files (ipxe-boot and ipxe-boot-efi)

### Cluster Metrics Display
In newer versions this is not enabled by default and must be enabled inside Addons section. The metrics from main dashboard are provided by Grafana.
All data is collected by Prometheus and displayed in Grafana.

### VM Backup Target
Harvester provides a backup and restore functionality for VMs. The backup targer can be either NFS server or an S3 bucket. The backup target functionality is inherited from the backup feature of the embedded Longhorn cluster.

> Restore to New Cluster
> + 