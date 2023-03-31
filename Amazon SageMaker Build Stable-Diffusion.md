# 使用Amazon SageMaker构建Stable-Diffusion

# 前提条件

## 区域: `ap-northeast-1(东京)`

## 服务配额
Service-Quota配额控制台:https://ap-northeast-1.console.aws.amazon.com/servicequotas/home/services/sagemaker/quotas
**本次实验需要用到GPU实例，如果您使用的是个人账号，请先确认您有`ml.g4dn.xlarge`的服务配额**

![Service Quotas](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/service%20quotas.png?raw=true)

### **申请提高配额**
**选中需要提高的服务配额，单击右上角 `请求增加配额`**
![Service Quotas-add-1](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/apply-add-1.png?raw=true)

**更改配额值为 `1`**
![Service Quotas-add-2](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/apply-add-2.png?raw=true)

# 创建Amazon SageMaker Notebook实例

## 打开Amazon SageMaker控制台
**[直达链接:https://ap-northeast-1.console.aws.amazon.com/sagemaker/home?region=ap-northeast-1](https://ap-northeast-1.console.aws.amazon.com/sagemaker/home?region=ap-northeast-1)**

![SageMaker Console](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/SageMaker%20Console.png?raw=true)

## 创建Notebook实例

**需要滑动左侧的服务框，找到`笔记本`-->`笔记本实例`---右上角`创建笔记本实例`**
![Notebook-create-1](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/notebook-create-1.png?raw=true)

**设置笔记本实例的名称、选择笔记本实例、以及存储的大小**
![Notebook-create-2](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/notebook-create-2.png?raw=true)

**对于权限和加密，点击`角色下拉框`，然后点击 `创建新角色`
![Notebook-create-3](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/notebook-create-3.png?raw=true)

**在本次实验中需要用到S3存储桶来存放模型文件，在此处可以选择`任意存储桶`或者`特定的存储桶`**
![Notebook-create-4](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/notebook-create-4.png?raw=true)

**点击创建笔记本实例**
![Notebook-create-5](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/notebook-create-5.png?raw=true)

**等待大约4分钟左右，笔记本实例的状态为`InService`，我们就可以点击`JupyterLab`进行实验了**
![Notebook-create-6](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/notebook-create-6.png?raw=true)


# 构建AIGC环境

**查看Jupyter Lab控制台，选择最下面的 `Terminal` **
![AIGC-1](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/AIGC-1.png?raw=true)

**在此处我们需要下载本次实验的Notebook代码文件**
```bash
cd SageMaker
wget https://static.us-east-1.prod.workshops.aws/public/73ea3a9f-37c8-4d01-ae4e-07cf6313adac/static/code/notebook-stable-diffusion-ssh-inference.ipynb
```
![AIGC-2](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/AIGC-2.png?raw=true)

**双击打开刚刚下载的Notebook文件，需要注意我们要选择内核，请选择`conda_pytorch_p39`**
![AIGC-3](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/AIGC-3.png?raw=true)

**修改提示词，生成新图片**
![AIGC-4](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/AIGC-4.png?raw=true)


# 利用Amazon Cloud 9 构建前后端Web应用

## 创建Cloud 9 环境

![cloud9-console](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/Cloud9-console.png?raw=true)

**根据自己的需求设置名称，选择实例的大小以及实例的系统**
![cloud9-create-1](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/Cloud9-create-1.png?raw=true)
![cloud9-create-2](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/Cloud9-create-2.png?raw=true)
![cloud9-create-3](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/Cloud9-create-3.png?raw=true)


## 构建Web应用

**这里步骤就是 `下包解压装依赖,服务一跑出图片`**
```bash
wget https://static.us-east-1.prod.workshops.aws/public/73ea3a9f-37c8-4d01-ae4e-07cf6313adac/static/code/SampleWebApp.zip
unzip SampleWebApp.zip
pip install Flask boto3
```

**等待Web应用运行起来后，开始使用描述词来生成我们的图片**
![cloud9-web-1](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/cloud9-web-1.png?raw=true)

![cloud9-web-2](https://github.com/flying1574/Amazon-SageMaker-Hands-on/blob/main/images/cloud9-web-2.png?raw=true)




