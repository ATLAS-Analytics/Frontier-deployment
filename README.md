# Frontier-deployment
for Frontier FluxCD deployment

need this:

flux create source git frontier-latest \
--url=https://github.com/ATLAS-Analytics/Frontier-deployment \
--branch=main \
--interval=3m \
--export \
> source.yaml

flux create kustomization frontier-latest \
--source=frontier-latest \
--path="./deploy/prod/" \
--prune=false \
--interval=5m \
--export \
> kustomization.yaml