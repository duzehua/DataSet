# **Dataset Description**

## **Introduction**

The dataset is composed of four sub-datasets, and the load category name contained in each sub-dataset is saved in the ‘labels.txt’ document under each sub-dataset folder. The data of each type of load are relatively ideal and pure operating environment to avoid the interference of other factors in the load identification process. We control the proportion of similar electrical appliances to construct a subset, because as far as we know, the classification of similar electrical appliances is a more difficult problem in the load identification algorithm. The main function of this dataset is to verify the separability of load classification algorithm for similar electrical appliances. Of course, the dataset does not include the features of long time-series that can provide power consumption rule capture, nor does it make the operation data waveforms of two different loads completely consistent (we think this is inseparable).

## **Dataset Partition**

Each sub-dataset contains the data of n (n=7, 10, 19, 23) appliances. Among them, 5500 cycles of operation data are extracted for each type of load, and the training set and test set are divided according to the ratio of 10:1. In order to ensure the reliability and stability of the load classification algorithm, we slice each sub-dataset and build a dataset (K0-K3) for 5-fold cross-validation, which is stored in four folders respectively.

## **Example**

Take the DataSet_0 corresponding to K0 as an example to explain the extraction method of the dataset:

### **Dataset import**

```python
import pickle

with open("./DataSet/train-data-K0.pkl", "rb") as f:
  train_data = pickle.load(f)

with open("./DataSet/val-data-K0.pkl", "rb") as f:
  val_data = pickle.load(f)

with open("./DataSet/test-data.pkl", "rb") as f:
  test_data = pickle.load(f)


```

### **Variable Description**

The data format of each variable is as follows:

```python
’train_data’={dict: 3}
    -->’original_data’ = {ndarray:(n1, 2, 1, 80)}
    -->’targets’ = {list: 92000}
    -->’classes’ = {‘list: 23’}
```

```python
’val_data’={dict: 3}
    -->’original_data’ = {ndarray:(n2, 2, 1, 80)}
    -->’targets’ = {list: 23000}
    -->’classes’ = {‘list: 23’}
```

```python
’test_data’={dict: 3}
    -->’original_data’ = {ndarray:(n3, 2, 1, 80)}
    -->’targets’ = {list: 11500}
    -->’classes’ = {‘list: 23’}
```

Among them, n1, n2 and n3 respectively represent the number of samples in training set, validation set and test set; classes represents the names of all 23 types of loads; targets is the load tag value corresponding to classes; original_data refers to the current and voltage data of the load. Each sample is represented by a three-dimensional tensor with the size of [2,1,80]. The first dimension represents the current cycle data with the size of [1,80], and the second dimension represents the voltage cycle data with the size of [1,80].

## **Schematic Diagram of Load Current and Voltage**

Finally, we randomly extract one cycle for visualization. The current and voltage data of 23 types of loads are shown as follows:

| ![](https://gitee.com/duzehua/pic-bed/raw/master/img/0.png)  | ![](https://gitee.com/duzehua/pic-bed/raw/master/img/1.png)  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Figure1 Notebook1                                            | Figure2 Notebook2                                            |
| ![](https://gitee.com/duzehua/pic-bed/raw/master/img/2.png)  | ![](https://gitee.com/duzehua/pic-bed/raw/master/img/3.png)  |
| Figure3 Refrigerator1                                        | Figure4 Refrigerator2                                        |
| ![](https://gitee.com/duzehua/pic-bed/raw/master/img/4.png)  | ![](https://gitee.com/duzehua/pic-bed/raw/master/img/5.png)  |
| Figure5 ElectricFan1                                         | Figure6 ElectricFan2                                         |
| ![](https://gitee.com/duzehua/pic-bed/raw/master/img/6.png)  | ![](https://gitee.com/duzehua/pic-bed/raw/master/img/7.png)  |
| Figure7 Vacuum                                               | Figure8 Ventilator                                           |
| ![](https://gitee.com/duzehua/pic-bed/raw/master/img/8.png)  | ![](https://gitee.com/duzehua/pic-bed/raw/master/img/9.png)  |
| Figure9 ElectricHeater1                                      | Figure10 ElectricHeater2                                     |
| ![](https://gitee.com/duzehua/pic-bed/raw/master/img/10.png) | ![](https://gitee.com/duzehua/pic-bed/raw/master/img/11.png) |
| Figure11 ElectricOven                                        | Figure12 ElectricKettle1                                     |
| ![](https://gitee.com/duzehua/pic-bed/raw/master/img/12.png) | ![](https://gitee.com/duzehua/pic-bed/raw/master/img/13.png) |
| Figure13 WaterDispenser                                      | Figure14 ElectricKettle2                                     |
| ![](https://gitee.com/duzehua/pic-bed/raw/master/img/14.png) | ![](https://gitee.com/duzehua/pic-bed/raw/master/img/15.png) |
| Figure15 ElectricCooker                                      | Figure16 Monitor                                             |
| ![](https://gitee.com/duzehua/pic-bed/raw/master/img/16.png) | ![](https://gitee.com/duzehua/pic-bed/raw/master/img/17.png) |
| Figure17 Television                                          | Figure18 AirPurifier                                         |
| ![](https://gitee.com/duzehua/pic-bed/raw/master/img/18.png) | ![](https://gitee.com/duzehua/pic-bed/raw/master/img/19.png) |
| Figure19 MainFrame                                           | Figure20 InductionCooker                                     |
| ![](https://gitee.com/duzehua/pic-bed/raw/master/img/20.png) | ![](https://gitee.com/duzehua/pic-bed/raw/master/img/21.png) |
| Figure21 Oxygenerator                                        | Figure22 Tablet1                                             |
| ![](https://gitee.com/duzehua/pic-bed/raw/master/img/22.png) |                                                              |
| Figure23 Tablet2                                             |                                                              |

