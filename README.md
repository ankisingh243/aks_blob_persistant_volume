# Azure Blob storage in Azure Kubernetes Service (AKS) as Persistant Volume
Applications running in Azure Kubernetes Service (AKS) may need to store and retrieve data. While some application workloads can use local, fast storage on unneeded, emptied nodes, others require storage that persists on more regular data volumes within the Azure platform.

A persistent volume (PV) is a storage resource created and managed by the Kubernetes API that can exist beyond the lifetime of an individual pod.
This article shows the steps for creating and mounting a blob storage using Azure Blob storage Container Storage Interface (CSI) driver on a AKS cluster.

Following document provide details for various types of storage available for AKS  :- https://learn.microsoft.com/en-us/azure/aks/concepts-storage
## STEPS
1. Create AKS cluster following document if you dont have one :- https://learn.microsoft.com/en-us/azure/aks/learn/quick-kubernetes-deploy-cli
2. Enable CSI driver for new or existing AKS cluster :- https://learn.microsoft.com/en-us/azure/aks/azure-blob-csi?tabs=NFS#enable-csi-driver-on-a-new-or-existing-aks-cluster
3. Create a persistent volume claim using built-in storage class.A persistent volume claim (PVC) uses the storage class object to dynamically provision an Azure Blob storage container.:-https://learn.microsoft.com/en-us/azure/aks/azure-csi-blob-storage-provision?tabs=mount-nfs%2Csecret#create-a-persistent-volume-claim-using-built-in-storage-class
4. Use the persistent volume claim.:- https://learn.microsoft.com/en-us/azure/aks/azure-csi-blob-storage-provision?tabs=mount-nfs%2Csecret#use-the-persistent-volume-claim
5. <p>After the pod is in the running state, run the following command to create a new file called test.txt<br> <strong>kubectl exec mypod -- touch /mnt/blob/test.txt </strong></p>
6. <p>Validate the disk is correctly mounted, run the following command, and verify you see the test.txt file in the output.<br><strong>kubectl exec mypod -- ls /mnt/blob</strong></p>
7. Validate on azure portal to check the blob created and file test.txt in the blob container.
8. <p>Upload a file on blob container through Portal.check again if you can see this uploaded file on Pod mounted volume.<br><strong>kubectl exec mypod -- ls /mnt/blob</strong></p>
   
    

