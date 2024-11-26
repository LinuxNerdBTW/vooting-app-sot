# Define Source SOT

flux create source git vooting-app-sot \
    --url=https://github.com/LinuxNerdBTW/vooting-app-sot.git \
    --branch=main \
    --interval=30s \
    --export > ./deploy/flux_source.yaml


# Apply above source SOT using kustomization controller
flux create kustomization vooting-app-sot \
    --source=vooting-app-sot \
    --path="./deploy/" \
    --prune=true \
    --validation=client \
    --interval=30s \
    --export > ./deploy/flux_sync.yaml