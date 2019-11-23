# aws-eks-efs

    kubectl exec -it efs sh
    cd /opt
    ls
    mkdir phani
    exit


### Mount the spcific folder to pod ###

    apiVersion: v1
    kind: Pod
    metadata:
      name: app1
    spec:
      containers:
      - name: app1
        image: nginx:alpine
        volumeMounts:
        - name: persistent-storage
          mountPath: /user/share/nginx/html
      volumes:
      - name: persistent-storage
        nfs:
          server: fs-6f79f3a4.efs.eu-west-1.amazonaws.com
          path: /phani
