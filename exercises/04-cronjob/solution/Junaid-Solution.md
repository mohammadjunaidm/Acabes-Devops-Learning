Applied the above yaml by changing the name of it.

kubectl apply -f junaid-cronjob.yaml
 
Verified the cj creation using the below command

kubectl get cj
NAME                  SCHEDULE    TIMEZONE   SUSPEND   ACTIVE   LAST SCHEDULE   AGE
junaid-current-date   * * * * *   <none>     False     0        14s             4m40s

Checked the cronjob execution via pod creation 

kubectl get pods --show-labels
NAME                                 READY   STATUS      RESTARTS   AGE    LABELS
junaid-current-date-29468724-dcxqv   0/1     Completed   0          3m2s   batch.kubernetes.io/controller-uid=fdc40ff6-d6b4-4ac0-b4b3-53a7ceecc013,batch.kubernetes.io/job-name=junaid-current-date-29468724,controller-uid=fdc40ff6-d6b4-4ac0-b4b3-53a7ceecc013,job-name=junaid-current-date-29468724
junaid-current-date-29468725-k9dhg   0/1     Completed   0          2m2s   batch.kubernetes.io/controller-uid=8c2b8560-98ba-410d-a47f-e52d6990e343,batch.kubernetes.io/job-name=junaid-current-date-29468725,controller-uid=8c2b8560-98ba-410d-a47f-e52d6990e343,job-name=junaid-current-date-29468725
junaid-current-date-29468726-pwvbt   0/1     Completed   0          62s    batch.kubernetes.io/controller-uid=77694a0b-57a2-4f5d-a3ae-5499335a6e7a,batch.kubernetes.io/job-name=junaid-current-date-29468726,controller-uid=77694a0b-57a2-4f5d-a3ae-5499335a6e7a,job-name=junaid-current-date-29468726
junaid-current-date-29468727-ml2d4   0/1     Completed   0          2s     batch.kubernetes.io/controller-uid=354374d3-f60b-42b1-adc4-a321216e8da3,batch.kubernetes.io/job-name=junaid-current-date-29468727,controller-uid=354374d3-f60b-42b1-adc4-a321216e8da3,job-name=junaid-current-date-29468727

Verified the logs of the pod

kubectl logs junaid-current-date-29468726-pwvbt
Current date: Sun Jan 11 09:26:02 UTC 2026

Verified the successful job history limit 

kubectl get cronjobs junaid-current-date -o yaml | grep successfulJobsHistoryLimit:
  successfulJobsHistoryLimit: 3

Deleted the cronjob

kubectl delete cj junaid-current-date
cronjob.batch "junaid-current-date" deleted from default namespace
