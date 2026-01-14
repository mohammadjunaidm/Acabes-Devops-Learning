  Wrote the below yaml and verified transformer container which continuously write a new file every 20 seconds.
    
    api version: v1
    kind: pod
    metadata:
      name: junaid-adapter
    
    spec:
      container:
       -name: app
       -image: busybox
       -args:
        -/bin/sh
        - -c
        - 'while true; do echo "$(date) | $(du -sh ~)" >> /var/logs/diskspace.txt; sleep 5; done;'
    
    VolumeMount:
      - name: junaidvolume
        mountPath: /var/usr
    
    
        -name: transformer
        -image: busybox
        -args:
          -/bin/sh
          - -c
          - 'sleep 20; while true; do while read LINE; do echo "$LINE" | cut -f2 -d"|" >> $(date +%Y-%m-%d-%H-%M-%S)-transformed.txt; done < /var/logs/diskspace.txt; sleep 20; done;'
          
    VolumeMount:
      - name: junaidvolume
        mountPath: /var/usr
        
    volume:
      -name: junaidvolume
      emptyDir: {}
      
