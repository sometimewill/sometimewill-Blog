### 获取xml中的节点内容时

    # 当要获取属性值时，用attrib方法。
    # 当要获取节点值时，用text方法。
    # 当要获取节点名时，用tag方法。
    
    例子：
    <Objects>
    <Object ElementType="Schedule" ID="948200890" Action="REGIST" Code="948200890">
    <Property Name="ChannelCode">HD-4000k-1080P-cctv1</Property>
    <Property Name="ChannelID">HD-4000k-1080P-cctv1</Property>
    <Property Name="Description">电视剧</Property>
    <Property Name="Duration">005100</Property>
    <Property Name="Genre"/>
    <Property Name="ObjectCode"/>
    <Property Name="ObjectType"/>
    <Property Name="ProgramName">电视剧</Property>
    <Property Name="SearchName"/>
    <Property Name="SourceType"/>
    
        Objects = root.findall('Objects/Object')  # 查找所有根目录下的property的子节点
    for Object_list in Objects:  # 对查找后的结果遍历
        if Object_list.attrib.get('Action') == 'REGIST':  # 筛选action为REGIST的 刨去DELETE状态的
            # print(Object_list.attrib.get('Code'))
            for Object in Object_list:
                temp = Object.attrib.get('Name')

                for i in range(0, len(temp), 1):
                    temp_dict = {
                        temp: Object.text
                    }
    