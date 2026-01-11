Created the job yaml 

Applied it using this command
Kubectl apply -f junaid-hash-job.yaml

Verified using the below command
kubectl get jobs

kubectl get jobs
NAME          STATUS    COMPLETIONS   DURATION   AGE
junaid-hash   Running   0/5           7s         7s

Verified the job pods 

kubectl get pods | grep "junaid-hash-"
junaid-hash-8wg2z   0/1     Completed   0          33s
junaid-hash-9pwzs   0/1     Completed   0          21s
junaid-hash-jn6qd   0/1     Completed   0          18s
junaid-hash-pqqbp   0/1     Completed   0          33s
junaid-hash-rb28t   0/1     Completed   0          22s


Verified the b64 contents by checking the pod logs

kubectl get pods | grep "junaid-hash-"
junaid-hash-8wg2z   0/1     Completed   0          33s
junaid-hash-9pwzs   0/1     Completed   0          21s
junaid-hash-jn6qd   0/1     Completed   0          18s
junaid-hash-pqqbp   0/1     Completed   0          33s
junaid-hash-rb28t   0/1     Completed   0          22s


Deleted the job using the below command 

kubectl delete job junaid-hash
job.batch "junaid-hash" deleted from default namespace
