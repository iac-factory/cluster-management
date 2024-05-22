# cluster-management

Kubernetes GitOps for Management Cluster(s)

## New Cluster Provisioning

```bash
flux bootstrap github --repository "https://github.com/iac-factory/cluster-management" \
    --owner "iac-factory" \
    --private "false" \
    --personal "false" \
    --path "clusters/local"
```

Add `kustomization.yaml` to new cluster directory.

```bash
cat << EOF > ./vendors/cluster-management/clusters/local/kustomization.yaml
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
resources: []
EOF
```

Update.

```bash
git submodule foreach "git add . && git commit --message \"Git Submodule Update(s)\" && git push -u origin HEAD:main" 
```

```bash
git submodule update --remote --recursive
```
