# Pyg Cora

[_Documentation generated by Documatic_](https://www.documatic.com)

<!---Documatic-section-Codebase Structure-start--->
## Codebase Structure

<!---Documatic-block-system_architecture-start--->
```mermaid
None
```
<!---Documatic-block-system_architecture-end--->

# #
<!---Documatic-section-Codebase Structure-end--->

<!---Documatic-section-PyG.cora.layer.gcn_norm-start--->
## PyG.cora.layer.gcn_norm

<!---Documatic-section-gcn_norm-start--->
<!---Documatic-block-PyG.cora.layer.gcn_norm-start--->
<details>
	<summary><code>PyG.cora.layer.gcn_norm</code> code snippet</summary>

```python
@torch.jit._overload
def gcn_norm(edge_index, edge_weight=None, num_nodes=None, improved=False, add_self_loops=True, dtype=None):
    pass
```
</details>
<!---Documatic-block-PyG.cora.layer.gcn_norm-end--->
<!---Documatic-section-gcn_norm-end--->

# #
<!---Documatic-section-PyG.cora.layer.gcn_norm-end--->

<!---Documatic-section-PyG.cora.cora.train-start--->
## PyG.cora.cora.train

<!---Documatic-section-train-start--->
<!---Documatic-block-PyG.cora.cora.train-start--->
<details>
	<summary><code>PyG.cora.cora.train</code> code snippet</summary>

```python
def train():
    model.train()
    optimizer.zero_grad()
    loss_train = F.nll_loss(model()[data.train_mask], data.y[data.train_mask])
    loss_train.backward()
    optimizer.step()
    return loss_train.item()
```
</details>
<!---Documatic-block-PyG.cora.cora.train-end--->
<!---Documatic-section-train-end--->

# #
<!---Documatic-section-PyG.cora.cora.train-end--->

<!---Documatic-section-PyG.cora.cora.test-start--->
## PyG.cora.cora.test

<!---Documatic-section-test-start--->
<!---Documatic-block-PyG.cora.cora.test-start--->
<details>
	<summary><code>PyG.cora.cora.test</code> code snippet</summary>

```python
@torch.no_grad()
def test():
    model.eval()
    logits = model()
    loss_val = F.nll_loss(logits[data.val_mask], data.y[data.val_mask]).item()
    for (_, mask) in data('test_mask'):
        pred = logits[mask].max(1)[1]
        accs = pred.eq(data.y[mask]).sum().item() / mask.sum().item()
    return (loss_val, accs)
```
</details>
<!---Documatic-block-PyG.cora.cora.test-end--->
<!---Documatic-section-test-end--->

# #
<!---Documatic-section-PyG.cora.cora.test-end--->

[_Documentation generated by Documatic_](https://www.documatic.com)