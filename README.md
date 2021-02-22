# Commands to create a Test KOPS Cluster

1. Download the kops configuration file
```shell
wget https://raw.githubusercontent.com/prakarsh-dt/kops-cluster/789a2cc1b0bbac83c468d1edf23584e86a0e1b0f/test/kops-spots-use1-cluster-config.yaml
```

2. Set the KOPS_STATE_STORE environment variable with the statestore bucket
```shell
export KOPS_STATE_STORE="s3://statestore-bucket-name"
```

3. Create the cluster with the configs from the downloaded file (Please change the cluster name/other configs if you have to before issuing the **kops create** command)
To change the cluster name please replace cluster name mentioned in the nodegroup labels as well.
```kops create secret --name test.devtron.k8s.local sshpublickey admin -i ~/.ssh/id_rsa.pub
kops create -f kops-spots-use1-cluster-config.yaml --yes
```

4. To delete the cluster please use the following command (make sure the KOPS_STATE_STORE environment variable is set)
```
kops delete cluster test.devtron.k8s.local --yes
```
