# Frontier-deployment
for Frontier FluxCD deployment

need to run this:

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

To actually start it at the cluster do:

flux create source git frontier-latest \
--url=https://github.com/ATLAS-Analytics/Frontier-deployment \
--branch=main --interval=3m

flux create kustomization frontier-latest \
--source=frontier-latest \
--path="./deploy/prod/" --prune=false --interval=5m


flux reconcile kustomization  --with-source frontier-latest

flux get kustomizations --watch