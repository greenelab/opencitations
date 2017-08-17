# Processing OpenCitations Data

This repository processes the [OpenCitations data](http://opencitations.net/download) to make it more user-friendly and concise.
The primary output is [`data/citations-doi.tsv.xz`](data/citations-doi.tsv.xz), which is a catalog of DOI-to-DOI citations.
The file is formated like:

| source_doi | target_doi |
|------------|------------|
| 10.1002/14651858.cd002244.pub4 | 10.1001/archneur.1990.00530120057010 |
| 10.1002/14651858.cd002244.pub4 | 10.1002/14651858.cd002244 |
| 10.1002/14651858.cd002244.pub4 | 10.1002/14651858.cd002244.pub2 |
| 10.1002/14651858.cd012199 | 10.1001/jama.295.6.676 |
| 10.1002/14651858.cd012199 | 10.1001/jama.299.16.1937 |
| 10.1002/14651858.cd012199 | 10.1002/14651858.cd000371.pub6 |
| 10.1002/14651858.cd012199 | 10.1002/14651858.cd009382.pub2 |

All DOIs are lowercase.
Quality control steps were performed on the DOIs to remove clearly incorrect DOIs.
However, for best results, we recommend users intersect these DOIs with a catalog of valid DOIs to remove any remaining errant DOIs.

## Execution

The downloading and processing of the OpenCitations data is accomplished by sequentially running the notebooks in this repository.
To update the pipeline to use newer versions of OpenCitations data, one should update the figshare article IDs in [`01.download.ipynb`](01.download.ipynb).

## Environment

This repository uses [conda](http://conda.pydata.org/docs/) to manage its environment as specified in [`environment.yml`](environment.yml).
Install the environment with:

```sh
conda env create --file=environment.yml
```

Then use `source activate opencitations` and `source deactivate` to activate or deactivate the environment.
On windows, use `activate opencitations` and `deactivate` instead.

In addition, to the conda environment, users will need to install the [Disk ARchive](http://dar.linux.free.fr/) (`dar`) utility to their system.
