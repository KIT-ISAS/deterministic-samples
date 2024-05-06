# deterministic-samples
Library of deterministic samples, to be downloaded for use in filtering, control, and cubature algorithms. 

## LCD Sampling
- Literature
    - LCD in general: https://ieeexplore.ieee.org/document/4648104
    - DMA of Gaussians: https://ieeexplore.ieee.org/document/5400649
    - S2KF: https://isif.org/media/smart-sampling-kalman-filter-symmetric-samples
- Code
    - https://nonlinearestimation.bitbucket.io/
    - https://codeocean.com/capsule/1886845/tree

## Usage
### Python
```
import pandas
from urllib.error import HTTPError

# Samples Cache
data_dict = {}

# Get Samples from Cache (and load if not available)
def get_data(url):
    if not (url in data_dict):
        try:
            data = pandas.read_csv(url, header=None).to_numpy()
        except HTTPError:
            # URL doesn't exist, data not available
            data = None
        data_dict[url] = data
    return data_dict[url]

def url_SND_LCD(D, L):
    return f'https://raw.githubusercontent.com/KIT-ISAS/deterministic-samples-csv/main/standard-normal/glcd/D{D}-N{L}.csv'

# get 100 2D standard normal samples
X = get_data(url_SND_LCD(2, 100))
```
