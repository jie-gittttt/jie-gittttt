# jie-gittttt

A student preparing for Fall 2027 graduate applications. This is where I keep coursework,
research and study materials.

Most of it is systems work — parallel and distributed computing, and machine learning
implemented close enough to the metal that the cost of each design decision is measurable.

---

## Featured

### [adaptive-gpr-stock-forecasting](https://github.com/jie-gittttt/adaptive-gpr-stock-forecasting)

**Gaussian process regression assumes its kernel is stationary over the entire training series.
Stock prices are not.**

Fit the kernel on the 2021 bull market, forecast into the early-2022 crash, and the model predicts
a rise the whole way down — with no mechanism to notice it is wrong, because nothing in a fixed
prior represents *"the regime has changed."* This project measures what that costs and how much a
volatility-aware adaptive window can recover.

| | |
| :--- | :--- |
| **The failure** | Under a long/flat strategy, the static baseline forfeits **78.38%** of the oracle's return on TSLA over ~40 trading days. NVDA: 70.57%. |
| **The fix** | A window that contracts when volatility rises, bounded 15–200 days, paired with a Rational Quadratic kernel. |
| **What it wins** | Lowest Regret on GOOGL and MSFT; lowest RMSE on MSFT and NDX; highest direction accuracy on 3 of 5 tickers. MSFT DA reaches 56.4% vs 51.3% static. |
| **What it costs** | 2–6× cheaper than the fixed 200-day window it beats — but an order of magnitude slower than simply not retraining. |
| **Where it still loses** | On TSLA it is beaten on both metrics by a fixed 200-day window. Discarding data buys stability; on a persistently volatile instrument it discards too much. |

Four configurations × two market regimes, five tickers, ten years of NASDAQ data. Every number in
the README is reproduced by a script, and the scripts are checked against committed raw output.

**[Read the full write-up →](https://github.com/jie-gittttt/adaptive-gpr-stock-forecasting)**

---

## Repositories

| Repository | What's in it |
| :--- | :--- |
| **[adaptive-gpr-stock-forecasting](https://github.com/jie-gittttt/adaptive-gpr-stock-forecasting)** | Gaussian process regression on non-stationary price series — four configurations, two regimes, reproducible end to end |
| **[parallel-computing](https://github.com/jie-gittttt/parallel-computing)** | MPI message passing · Pthread / OpenMP shared memory · CUDA heterogeneous computing — plus **nine interactive demos** of the mechanisms |
| **[stochastic-processes](https://github.com/jie-gittttt/stochastic-processes)** | Course collection: information cascades in social networks, Brownian motion, and the GPR assignment that became the project above |
| **[DeepLearning-HW](https://github.com/jie-gittttt/DeepLearning-HW)** | Fully-connected networks, CNN image classification, RNN poetry generation, Seq2Seq with attention — classic architectures implemented from scratch |

## Interactive visualizations

**[jie-gittttt.github.io/parallel-computing](https://jie-gittttt.github.io/parallel-computing/)**
— nine browser demos that let you watch each mechanism work: MPI loop interchange and matrix
transpose, three views of convolution from serial to optimized, and CUDA grid mapping, warp
access patterns, operator fusion and memory bandwidth. No installation and no server; they
render in the page.

## Also worth reading

- **MPI matrix multiplication** — the decisive speedup did not come from adding processes. It
  came from reordering the loops so memory access follows the cache. On a single process that
  was 1.36×; combined with 4 processes, 6.29×, with the end-to-end pipeline at 8.57×.
  → [parallel-computing/01-mpi-matrix-multiplication](https://github.com/jie-gittttt/parallel-computing/tree/main/01-mpi-matrix-multiplication)

- **CUDA convolution** — fusing two kernels into one cut kernel time from 0.230 ms to 0.180 ms.
  The kernel was **0.03%** of the 187.6 ms pipeline; the other 99.97% was PCIe transfer and disk
  I/O. Further kernel optimization was pointless, and the measurement is what made that clear.
  → [parallel-computing/03-cuda-convolution-pooling](https://github.com/jie-gittttt/parallel-computing/tree/main/03-cuda-convolution-pooling)

## Stack

**Languages** Python · C++ · CUDA · SQL
**ML** PyTorch · TensorFlow · scikit-learn · NumPy · pandas
**Parallel** MPI · OpenMP · Pthreads · CUDA
**Other** Git · Linux · LaTeX

---

# 中文

一名准备 27Fall 申请的学生。这里存放我的课程作业、科研与学习资料。

内容以系统方向为主——并行与分布式计算，以及实现得足够接近底层、因而每一个设计决策的代价
都可被测量的机器学习。

---

## 精选项目

### [adaptive-gpr-stock-forecasting](https://github.com/jie-gittttt/adaptive-gpr-stock-forecasting)

**高斯过程回归假设它的核函数在整条训练序列上平稳。股价不是。**

用 2021 年牛市拟合核函数，再去预测 2022 年初的崩盘，模型会一路预测上涨——
而且**没有任何机制察觉自己错了**，因为固定的先验里不包含「市场性质已经变了」这件事。
本项目测量这个代价有多大，以及一个波动率感知的自适应窗口能挽回其中多少。

| | |
| :--- | :--- |
| **失效** | 在「涨则做多、否则空仓」策略下，静态基线在约 40 个交易日内放弃了上帝视角收益的 **78.38%**（TSLA）。NVDA 为 70.57%。 |
| **应对** | 波动率抬升时收缩的窗口，限制在 15–200 日，配合 Rational Quadratic 核。 |
| **赢在哪里** | GOOGL 与 MSFT 的 Regret 最低；MSFT 与 NDX 的 RMSE 最低；五支标的中三支的 DA 最高。MSFT 的 DA 达 56.4%，对比静态基线 51.3%。 |
| **代价** | 比它所战胜的固定 200 日窗口便宜 2–6 倍——但比「干脆不重训」慢一个数量级。 |
| **仍在哪里输** | 在 TSLA 上两项指标都不及固定 200 日窗口。丢弃数据换来稳定性，而在一个波动率长期偏高的标的上，它丢得太多了。 |

四种配置 × 两种市场状态，五支标的，十年 NASDAQ 数据。README 中的每一个数字都由脚本复现，
脚本的输出与提交的原始记录逐组对照。

**[阅读完整说明 →](https://github.com/jie-gittttt/adaptive-gpr-stock-forecasting)**

---

## 仓库

| 仓库 | 内容 |
| :--- | :--- |
| **[adaptive-gpr-stock-forecasting](https://github.com/jie-gittttt/adaptive-gpr-stock-forecasting)** | 非平稳价格序列上的高斯过程回归——四种配置、两种市场状态、端到端可复现 |
| **[parallel-computing](https://github.com/jie-gittttt/parallel-computing)** | MPI 消息传递 · Pthread / OpenMP 共享内存 · CUDA 异构计算——外加 **9 个交互式原理演示** |
| **[stochastic-processes](https://github.com/jie-gittttt/stochastic-processes)** | 课程合集：社交网络信息级联、布朗运动，以及后来独立成仓的那次 GPR 作业 |
| **[DeepLearning-HW](https://github.com/jie-gittttt/DeepLearning-HW)** | 全连接网络、CNN 图像分类、RNN 古诗生成、Seq2Seq 与注意力机制——经典结构的手写实现 |

## 交互式原理演示

**[jie-gittttt.github.io/parallel-computing](https://jie-gittttt.github.io/parallel-computing/)**
——九个浏览器内的交互演示，可以直观看到每种并行机制如何工作：MPI 的循环交换与矩阵转置、
卷积从串行到优化版本的三个视角，以及 CUDA 的网格映射、warp 访存模式、算子融合与显存带宽。
无需安装、不需要服务器，打开即用。

## 同样值得一读

- **MPI 矩阵乘法**——决定性的加速并非来自增加进程，而是来自重排循环顺序使访存符合缓存。
  单进程上这一步就是 1.36×；配合 4 进程达 6.29×，端到端流水线 8.57×。

- **CUDA 卷积**——把两个 kernel 融合成一个，kernel 时间从 0.230 ms 降到 0.180 ms。
  但 kernel 只占 187.6 ms 流水线的 **0.03%**，其余 99.97% 是 PCIe 传输与磁盘 I/O。
  继续优化 kernel 没有意义——是测量让这一点变得清楚。

## 技术栈

**语言** Python · C++ · CUDA · SQL
**机器学习** PyTorch · TensorFlow · scikit-learn · NumPy · pandas
**并行** MPI · OpenMP · Pthreads · CUDA
**其他** Git · Linux · LaTeX
