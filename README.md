### 主要有两个python脚本和一个uuids文件
#### 1、getuuids.py
脚本功能为判断此时所有的频道是否有缺失
需要修改信息为URL_UUID，F_UUID，W_UUID，W_ERROR，template

    第17行的 URL_UUID为获取某个模板的此时所有频道信息(修改域名)
    第19行F_UUID为uuids文件中频道信息与接口获取的频道信息是否有区别(修改路径)
    第21行W_UUID为第一次运行脚本时获取的所有频道信息作为标准(修改路径)
    第23行的W_ERROR为写入频道中比文件中多的频道信息并记录时间(修改路径)
    第50行uuids的文件路径(修改路径)
    第79行的template模板信息变更
如果未给uuids文件 可以打开46,47行注解并注释掉50-75行运行脚本后生成uuids文件，然后注解复原即可

#### 2、getallprogramlist.py
脚本功能为判断某个模板的所有频道今天明天是否连续
需要修改信息为URL_WEEKDAY，F_WEEKDAY，TEMPLATES，第142行uuids文件路径

    第16行的 URL_WEEKDAY为获取某个模板的单个频道信息(修改域名)
    第18行F_WEEKDAY为写入判断结果(修改路径)
    第14行TEMPLATES为模板信息(修改参数)
    第142行的为uuids文件的存放路径(修改路径)

#### 3、uuids
文件为存放频道列表的信息