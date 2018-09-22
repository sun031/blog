---
title: Tibet Pn plans
date: 2018-09-20 09:35:24
tags: [Tibet, Pn, ]
categories: Project
---

## 数据收集
1. 中国固定台网走时数据，已收集，待整理出研究区域的震相
1. ISC台站走时数据，已收集，待整理出研究区域的震相
2. 流动台站波形数据，已收集
2. 中国固定台站波形数据，已请科大程世华收集

## 震相数据拾取与处理
1. 流动台站波形数据拾取Pn，正在开展
2. 固定台站波形数据拾取Pn，

## 初始模型建立 -- 已完成 2018-09-22
### Moho -- 已完成 2018-09-20
1. Kennett提供的印度及西藏台站的数据，Tectonophysics
2. 中国固定台站下Moho厚度，He et al. 2014
3. 利用inverse distance weighting进行插值，100km范围内的台站
***
**Note:** 
I test two implementations to obtain the Moho. One is fetched from the Crust 1.0 model. The other is incorporating various results including receiver function of both permanent and portable stations, the Crust 1.0 model. The Moho from the Crust 1.0 model shows smooth depth variations, but not for the combined results of the 2nd scheme.

The Moho shows biases from the one read from the estimation of the initial P and S velocities.

**Just simply use the Moho from the Crust 1.0 model at first.**
 
***

### 速度模型，包括P波和S波初始速度模型 -- 已完成 2018-09-22
1. 尝试多个全球模型，LNLL P波模型，SL2013sv模型
2. 区域模型，但需要平滑，UCBoulder Tibet Model
3. 波速比将S波模型转换为P波模型
4. Lithos 1.0模型的波速比
***
**Note:** 
I have tested two schemes for converting S-wave velocity to P velocity. One is the direct conversion using the Vp/Vs ratio from the ak135 model. The other scheme is using the empirical formula given by Kennett et al. (2013) for building the AuSREM model. I found the anomalies of P velocity are strongly exaggerated using the first scheme, but the second scheme gives the geologically and geophysically reasonable P velocity.

**Use the empirical formula given by Kennett et al. (2013).**

***


## 地震事件重定位
1. 整理以前的程序
2. 写程序的帮助文档，用sphinx，生成PDF和HTML

### 技术细节
1. 去除定位后走时残差大的台站，e.g., >1.0s或者大于2倍标准差
2. 然后进行重新定位
3. 对地震事件进行多次重定位，给出4个参数平均值及其标准差
4. 使用4个参数平均值进行后续反演

## FMTOMO反演
1. 测试不同的阻尼和光滑因子: Liang et al. (2016EPSL)根据经验选取，Rawlinson et al. (2006JGR)选取不同的因子进行反演获得方差曲线后选取。
2. 不同初始速度模型进行反演
3. 对走时添加随机噪音，待定
4. 分辨率测试，预期分辨率2°X2°或者更大

## 构造线 -- 完成2018-09-20
1. 获取构造线数据
2. 南北向的rift数据
https://github.com/HimaTibetMap/HimaTibetMap

## 程序整理
1. **vs2vp**: Convert S velocity to P velocity using empirical formula of Kennett et al. (2013).
Lang: Fortran
Path: /home/weijias/disk1/proj/tibet/src/vs2vp


## 参考文献
1. 宋晓东PNAS2018文章
2. 钮凤林NatComm2017文章





