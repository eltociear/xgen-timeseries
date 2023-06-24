# Updating the example data

Metadata for XGenTS's example `InferenceData` objects (which are loadable by {func}`~XGenTS.load_XGenTS_data`) is stored in the [`XGenTS_example_data`](https://github.com/XGenTS-devs/XGenTS_example_data) repository.
This repo has been embedded into the `XGenTS` repo at `/XGenTS/data/example_data` using [git subtree](https://www.atlassian.com/git/tutorials/git-subtree) with the following command:

```bash
$ git subtree add --prefix XGenTS/data/example_data https://github.com/XGenTS-devs/XGenTS_example_data.git main --squash
```

When `XGenTS_example_data` is updated, the subtree within the `XGenTS` repo also needs to be updated with the following command:

```bash
$ git subtree pull --prefix XGenTS/data/example_data https://github.com/XGenTS-devs/XGenTS_example_data.git main --squash
```
