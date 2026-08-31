# Ex--6-AWS-Account-setup-and-S3-creation-
CLOUD STORAGE CREATION (S3) AND LAUNCHING AN (EC2) INSTANCE IN AWS
NAME: Avantika Krishnadas Kundooly
REG NO: 212224040040
Aim
To create and configure an Amazon Elastic Block Store (EBS) volume, attach and mount it to an Amazon EC2 instance, create a snapshot backup, and restore the snapshot to a new EBS volume.

Algorithm / Steps
Create a new Amazon EBS volume with a size of 1 GiB.
Select the same Availability Zone as the EC2 instance.
Attach the EBS volume to the EC2 instance using /dev/sdb.
Connect to the EC2 instance using AWS Systems Manager Session Manager.
Check the available storage using df -h.
Create an ext3 file system on the EBS volume.
Create the /mnt/data-store directory.
Mount the EBS volume to /mnt/data-store.
Configure /etc/fstab for automatic mounting.
Verify that the EBS volume is successfully mounted.
Create file.txt inside the mounted EBS volume.
Verify the contents of the created file.
Create an EBS snapshot named My Snapshot.
Delete file.txt from the original EBS volume.
Create a new EBS volume from the snapshot.
Attach the restored volume to the EC2 instance using /dev/sdc.
Create the /mnt/data-store2 directory.
Mount the restored volume to /mnt/data-store2.
Verify that file.txt has been successfully restored.
Program
1. Check Available Storage
df -h
2. Create an ext3 File System
sudo mkfs -t ext3 /dev/sdb
3. Create a Mount Directory
sudo mkdir /mnt/data-store
4. Mount the EBS Volume
sudo mount /dev/sdb /mnt/data-store
5. Configure Automatic Mounting
echo "/dev/sdb   /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab
6. View the File System Configuration
cat /etc/fstab
7. Verify the Mounted Volume
df -h
8. Create a File in the EBS Volume
sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"
### 8. Create a File in the EBS Volume


### 9. Read the File

```bash
cat /mnt/data-store/file.txt
10. Delete the File
sudo rm /mnt/data-store/file.txt
11. Verify File Deletion
ls /mnt/data-store/
12. Create a Mount Directory for the Restored Volume
sudo mkdir /mnt/data-store2
13. Mount the Restored EBS Volume
sudo mount /dev/sdc /mnt/data-store2
14. Verify Snapshot Restoration
ls /mnt/data-store2/
Expected output:

file.txt

Outputs

<img width="1600" height="807" alt="image" src="https://github.com/user-attachments/assets/9f36349e-9c45-4cb9-b89b-130a71d20884" />

<img width="1600" height="809" alt="image" src="https://github.com/user-attachments/assets/07fe060b-bb14-45b8-a897-0bf8931c0c13" />

<img width="1600" height="857" alt="image" src="https://github.com/user-attachments/assets/e4fa84fc-2104-4db5-9a74-825420ee0190" />

Result
Thus, an Amazon EBS volume was successfully created and attached to an Amazon EC2 instance. The volume was formatted with an ext3 file system, mounted, and used for storing data. An EBS snapshot was successfully created as a backup, and a new EBS volume was restored from the snapshot. The previously deleted file.txt was successfully recovered, demonstrating the backup and restore functionality of Amazon EBS.
