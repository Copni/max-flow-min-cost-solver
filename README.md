# Max-Flow / Min-Cost Solver

Three classic network flow algorithms implemented from scratch, plus a benchmark
that measures how each one actually scales.

## Algorithms

| Module | Algorithm | Problem |
| --- | --- | --- |
| `maxEK.py` | Edmonds-Karp | Maximum flow, BFS augmenting paths |
| `maxPR.py` | Push-relabel | Maximum flow, preflow with height labels |
| `minC.py` | Successive shortest paths | Minimum-cost flow at a given value |

Two different approaches to the same maximum-flow problem is the point: they
have different complexity profiles, and the benchmark shows where each one wins.

## Complexity benchmark

`complexity.py` generates random networks of increasing size, times each
algorithm and compares the measured growth against the theoretical bounds
(O(VE²) for Edmonds-Karp, O(V²E) for push-relabel).

## Usage

```bash
python main.py
```

The menu lets you pick one of the ten sample networks (`proposition_1.txt` …
`proposition_10.txt`), choose an algorithm, and follow the residual graph
evolving at each iteration.

## Input format

First line: number of vertices. Then the capacity matrix, and for min-cost
problems the cost matrix. Vertex `0` is the source, vertex `n-1` the sink.

## Implementation notes

The residual graph is updated in place rather than rebuilt at each iteration,
which keeps the per-augmentation cost down on the denser test networks.
