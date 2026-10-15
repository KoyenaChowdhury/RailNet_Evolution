# Evolution of the Indian Railway Network (1991–2024)

This repository contains Indian Railway Network (IRN) snapshots for 1991, 1997, 2000, 2005, 2009, 2015, 2017, and 2024, along with the corresponding train-route data used for network construction. The datasets support research on complex networks, network evolution, graph theory, and transportation systems.

## Data Sources

**India (old), 1991–2009:** Historical snapshots were reconstructed from Indian national railway timetable publications, *Trains at a Glance*, following Ghosh et al. (2012).

**India (new), 2015–2024:** The 2015 and 2017 snapshots were constructed from route-level records obtained from [data.gov.in](https://www.data.gov.in/), covering express trains with numbers beginning with 0, 1, or 2. The 2024 snapshot was constructed from schedule data collected from [RunningStatus.in](https://runningstatus.in/), following Chowdhury et al. (2026).

## Repository Contents

```text
edges_1991.edgelist
edges_1997.edgelist
edges_2000.edgelist
edges_2005.edgelist
edges_2009.edgelist
edges_2015.edgelist
edges_2017.edgelist
edges_2024.edgelist

Station_codes_2009.txt

Train_routes_1991.txt
Train_routes_1997.txt
Train_routes_2000.txt
Train_routes_2005.txt
Train_routes_2009.txt
Train_routes_2015_express.csv
Train_routes_2017_express.csv
Train_routes_Sep2024.csv
```

### File Descriptions

- **`edges_YEAR.edgelist`**: Constructed network snapshot for the corresponding year, represented as station pairs.
- **`Station_codes_2009.txt`**: Station-code information till 2009
- **`Train_routes_YEAR.txt`**: Historical train-route data for 1991–2009.
- **`Train_routes_2015_express.csv` and `Train_routes_2017_express.csv`**: Express train routes used to construct the respective snapshots.
- **`Train_routes_Sep2024.csv`**: Scheduled train-route data for September 2024.

## Graph Construction

Each snapshot is represented as an **undirected, unweighted simple graph** \(G_t=(V_t,E_t)\), where stations are nodes and an edge connects two stations if and only if they are consecutive stops on at least one scheduled train route. Duplicate connections are represented by a single edge.

Example using NetworkX:

```python
import networkx as nx

G = nx.read_edgelist(
    "edges_2024.edgelist",
    nodetype=str,
    create_using=nx.Graph()
)

print("Stations:", G.number_of_nodes())
print("Connections:", G.number_of_edges())
```

## References

1. Ghosh, S., Banerjee, A., and Ganguly, N. (2012). “Some insights on the recent spate of accidents in Indian Railways.” *Physica A: Statistical Mechanics and its Applications*, 391(9), 2917–2929.

2. Chowdhury, K., Koley, P., Chakraborty, A., and Ghosh, S. (2026). “RSTGCN: Railway-centric Spatio-Temporal Graph Convolutional Network for Train Delay Prediction.” *IEEE Transactions on Intelligent Transportation Systems*.

This repository supports research on railway network evolution, structural properties, connectivity, and complex network modeling.
