# 基于哈工大LTP4的三元组抽取
基本同刘焕勇老师的代码一致：https://github.com/taishan1994/ltp_triple_extraction
适用LTP4.2.0，主要解决了由于LTP更新至4.2.0版本带来的问题：
### [结构性变化] 将 LTP 拆分成 2 个部分，维护和训练更方便，结构更清晰
####    [Legacy 模型] 针对广大用户对于推理速度的需求，使用 Rust 重写了基于感知机的算法，准确率与 LTP3 版本相当，速度则是 LTP v3 的 3.55 倍，开启多线程更可获得 17.17 倍的速度提升，但目前仅支持分词、词性、命名实体三大任务
####    [深度学习模型] 即基于 PyTorch 实现的深度学习模型，支持全部的6大任务（分词/词性/命名实体/语义角色/依存句法/语义依存）
### [其他改进] 改进了模型训练方法
####    [共同] 提供了训练脚本和训练样例，使得用户能够更方便地使用私有的数据，自行训练个性化的模型
####    [深度学习模型] 采用 hydra 对训练过程进行配置，方便广大用户修改模型训练参数以及对 LTP 进行扩展（比如使用其他包中的 Module）
### [其他变化] 分词、依存句法分析 (Eisner) 和 语义依存分析 (Eisner) 任务的解码算法使用 Rust 实现，速度更快
### [新特性] 模型上传至 Huggingface Hub，支持自动下载，下载速度更快，并且支持用户自行上传自己训练的模型供LTP进行推理使用
### [破坏性变更] 改用 Pipeline API 进行推理，方便后续进行更深入的性能优化（如SDP和SDPG很大一部分是重叠的，重用可以加快推理速度），使用说明参见Github快速使用部分

参考如下：
介绍了新版ltp的存储方式：https://blog.csdn.net/Jacobsua/article/details/127960946
新版ltp的更新说明：https://github.com/HIT-SCIR/ltp
LTP文档：https://ltp.readthedocs.io/zh_CN/latest/introduction.html
