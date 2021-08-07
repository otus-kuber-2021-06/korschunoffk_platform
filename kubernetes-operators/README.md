**Results of the kubectl get jobs command:**
```bash
kkorshunov@devkk-k8s-vx-1:~/git_repos/korschunoffk_platform/kubernetes-operators/deploy$ kubectl get jobs
NAME                         COMPLETIONS   DURATION   AGE
backup-mysql-instance-job    1/1           2s         5m39s
restore-mysql-instance-job   1/1           5m46s      7m3s
```

**Database query**
```bash
kkorshunov@devkk-k8s-vx-1:~/git_repos2/korschunoffk_platform/kubernetes-operators$ export MYSQLPOD=$(kubectl get pods -l app=mysql-instance -o jsonpath="{.items[*].metadata.name}")
kkorshunov@devkk-k8s-vx-1:~/git_repos2/korschunoffk_platform/kubernetes-operators$ kubectl exec -it $MYSQLPOD -- mysql -potuspassword -e "select * from test;" otus-database
mysql: [Warning] Using a password on the command line interface can be insecure.
+----+-------------+
| id | name        |
+----+-------------+
|  1 | some data   |
|  2 | some data-2 |
+----+-------------+
```
