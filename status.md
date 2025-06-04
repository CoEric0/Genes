数据整理好了，里面有四个文件：
“Training_selected-genes.txt”和“testing_selected-genes.txt”是建模基于的基因list在不同临床样本中的表达量（已经均一化过）。
“Training_clinical-infor.txt”和“testing_clinical-infor.txt”是对应的临床信息，其中前两列分别是生存时间（OS.time）和生存状态（OS.state）。


另外，“Training_selected-genes.txt”和“testing_selected-genes.txt”中，后者少了一些基因，可以使用两个表格中共同的基因进行建模。“Training_clinical-infor.txt”和“testing_clinical-infor.txt”的生存时间和状态里有少许缺失值可以去除。


拜托帮试试建立预后模型


# env
```sh
conda create -n cgenes python=3.11

conda activate cgenes
```

gmdh


# clinical 数据说明
每个样本标记为 CGGA_xx ;
生存时间 
生存状态 0=alive，1=dead

- subtype	肿瘤亚型，“#N/A”说明数据缺失或还没分类。
- IDH stat	IDH基因的状态，“Mutant”是突变，“Wildtype”是正常。IDH突变常和胶质瘤类型、预后有关。

- PRS_type	肿瘤类型，“Primary”是原发性（第一次长出来的肿瘤。Recurrent是复发性，表示之前有过肿瘤，现在又长出来了。Secondary是继发性，表示肿瘤是由其他部位转移过来的。
- Histology	组织学类型，“A”可能指星形细胞瘤（一种胶质瘤类型），还有其他类型如少突胶质细胞瘤。

- Grade	WHO分级，表示肿瘤的恶性程度，“WHO II”是低级别（较温和），WHO III或IV是高级别（更严重）。

- Gender	性别，“Male”是男性，“Female”是女性。
- Radio_status	放疗状态，1表示接受过放疗，0表示没做过放疗。
- Chemo_status	化疗状态，1表示用过TMZ（一种化疗药），0表示没用过。

- 1p19q_codeletion_status	1p19q共缺失状态，“Codel”是有缺失，“Non-codel”是没缺失。NA 表示数据缺失。
- 2021classification_created By BZT	2021年 WHO 组织学分类，这是最新的肿瘤分类标准，同 Histology。


# selected-genes 数据说明
每个样本标记为 CGGA_xx（一一对应clinical）
表明不同基因在不同样本中的表达量，已经均一化过。

# 预后模型建立
