### WORKING WITH EBS
### NAME: AMRITA M
### REG NO: 212225040019
### Aim
To create and configure an Amazon Elastic Block Store (EBS) volume, attach and mount it to an Amazon EC2 instance, create a snapshot backup, and restore the snapshot to a new EBS volume.

### Algorithm / Steps
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

### Program
1. Check Available Storage
```
df -h
```
2. Create an ext3 File System
```
sudo mkfs -t ext3 /dev/sdb
```
3. Create a Mount Directory
```
sudo mkdir /mnt/data-store
```
4. Mount the EBS Volume
```
sudo mount /dev/sdb /mnt/data-store
```
5. Configure Automatic Mounting
```
echo "/dev/sdb   /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab
```
6. View the File System Configuration
```
cat /etc/fstab
```
7. Verify the Mounted Volume
```
df -h
```
8. Create a File in the EBS Volume
```
sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"
```
9. Read the File
```
cat /mnt/data-store/file.txt
```
10. Delete the File
```
sudo rm /mnt/data-store/file.txt
```
11. Verify File Deletion
```
ls /mnt/data-store/
```
12. Create a Mount Directory for the Restored Volume
```
sudo mkdir /mnt/data-store2
```
13. Mount the Restored EBS Volume
```
sudo mount /dev/sdc /mnt/data-store2
```
14. Verify Snapshot Restoration
```
ls /mnt/data-store2/
```
Expected output:

```
file.txt
```
Outputs
### Outputs

<img width="1920" height="1020" alt="Screenshot 2026-11-06 083713" src="https://github.com/user-attachments/assets/eca858d3-ddd5-4015-a551-9b287a83f167" />

<img width="1920" height="1020" alt="Screenshot 2026-11-06 083845" src="https://github.com/user-attachments/assets/e99bef9d-6fef-4473-a914-99db1d2eb070" />

<img width="1920" height="1020" alt="Screenshot 2026-11-06 084519" src="https://github.com/user-attachments/assets/0563e582-b02a-4797-ae81-c90f028c1fe2" />

<img width="1920" height="1020" alt="Screenshot 2026-11-06 084527" src="https://github.com/user-attachments/assets/a8c1a189-0c2e-4c8c-9f20-7a7477e9ad3a" />

<img width="1920" height="1020" alt="Screenshot 2026-11-06 084904" src="https://github.com/user-attachments/assets/67947d4d-6ccd-4a6f-b9de-c6a7eca1efbf" />

<img width="1920" height="1020" alt="Screenshot 2026-11-06 084948" src="https://github.com/user-attachments/assets/76e63e88-ae4e-4008-b06f-e537f33b9990" />

<img width="1920" height="1020" alt="Screenshot 2026-11-06 085127" src="https://github.com/user-attachments/assets/1bc31360-a185-4321-952d-9ef8ffa1a651" />

<img width="1920" height="1020" alt="Screenshot 2026-11-06 085136" src="https://github.com/user-attachments/assets/60252d66-1390-4de3-a25a-5a7f8284cfbc" />

<img width="1920" height="1020" alt="Screenshot 2026-11-06 085257" src="https://github.com/user-attachments/assets/8ea738b5-6c40-4bb0-8e1d-ab7aeeefdf79" />

<img width="1920" height="1020" alt="Screenshot 2026-11-06 083618" src="https://github.com/user-attachments/assets/c4467220-e867-4f2a-b4db-cddd318d5abd" />

<img width="1920" height="1020" alt="Screenshot 2026-11-06 083639" src="https://github.com/user-attachments/assets/ec8e8444-7f90-47e6-957d-f96789079c66" />

<img width="1920" height="1020" alt="Screenshot 2026-11-06 083713" src="https://github.com/user-attachments/assets/0389b63c-dd1e-48bc-9776-a4f34713af2e" />


<img width="1920" height="1020" alt="Screenshot 2026-11-06 083808" src="https://github.com/user-attachments/assets/36d0bc39-cc1e-4192-b281-fbe9341d0e36" />

<img width="1920" height="1020" alt="Screenshot 2026-11-06 084720" src="https://github.com/user-attachments/assets/21c55237-4c63-42e3-bdde-eb5339ae5544" />

<img width="1920" height="1020" alt="Screenshot 2026-11-06 085225" src="https://github.com/user-attachments/assets/2efd6219-63f3-4e1b-a934-c4104b19083a" />

<img width="1920" height="1020" alt="Screenshot 2026-11-06 085359" src="https://github.com/user-attachments/assets/afb094a8-92b6-4650-ba72-1520c3951c1b" />


### Result
Thus, an Amazon EBS volume was successfully created and attached to an Amazon EC2 instance. The volume was formatted with an ext3 file system, mounted, and used for storing data. An EBS snapshot was successfully created as a backup, and a new EBS volume was restored from the snapshot. The previously deleted file.txt was successfully recovered, demonstrating the backup and restore functionality of Amazon EBS.
