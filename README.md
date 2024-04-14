

# 明医 (MING)：中文医疗问诊大模型

<p align="center">
  <img src=".\img\bgimage.png" width=800px/>
</p>


<div align="center"><img src="https://img.shields.io/badge/Version-1.3--alpha-brightgreen"> <img src="https://img.shields.io/badge/Code%20License-Apache_2.0-green.svg"> <img src="https://img.shields.io/badge/python-3.9+-blue.svg"></div>

## 🌐项目简介

本项目开源了基于医疗指令微调的中文医疗问诊模型：**明医 (MING)**。目前模型的主要功能如下：

<!DOCTYPE html>
<html>
<body>
<table style="width: 100%;">
  <tr style="border-collapse: collapse; border: transparent;">
      <td style="width: 50%; border-collapse: collapse;border: transparent;"><img src=".\img\demo1.gif" alt="demo1"/></td>
      <td style="width: 50%; border-collapse: collapse;border: transparent;"><img src=".\img\demo2.gif" alt="demo2"/></td>
  </tr>
  <tr style="border-collapse: collapse; border: transparent;">
      <td style="width: 50%; border-collapse: collapse;border: transparent;" ><div align="center"><strong>医疗问答</strong>：对医疗问题进行解答，对案例进行分析。</div></td>
      <td style="width: 50%; border-collapse: collapse;border: transparent;"><div align="center"><strong>智能问诊</strong>：多轮问诊后给出诊断结果和建议。</div></td>
  </tr>
</table>
</body>
</html>

## 📄相关论文
* 基于多智能体交互的大语言模型多轮问诊自动评估框架
  
  [Automatic Interactive Evaluation for Large Language Models
with State Aware Patient Simulator](https://arxiv.org/pdf/2403.08495.pdf)

## 💫更新
* 🔥 [coming soon] Technical Report

* 🔥 [2024/04/14] 开源了基于Qwen1.5指令微调的专家混合模型MING-MOE

* [2024/03/14] 开源了基于Qwen1.5-1.8b指令微调的MING-1.8B

* [2023/07/25] 开源了基于bloomz-7b指令微调的MING-7B

* [2023/07/25] MedicalGPT-zh更名为**MING**

  

##  🔬开源模型

<!DOCTYPE html>
<html>
<head>
</head>
<body>
<table style="width: 80%;">
  <tr>
      <td style="width: 20%;"><div align="center"><strong>模型</strong></div></td>
      <td style="width: 20%;"><div align="center"><strong>基座</strong></div></td>
      <td style="width: 30%;"><div align="center"><strong>HuggingFace</strong></div></td>
  </tr>
  
  <tr>
      <td><center>MING-7B</center></td>
      <td><center><a href="https://huggingface.co/bigscience/bloomz-7b1-mt">bloomz-7b1-mt</a></center></td>
      <td><center>🤗<a href="https://huggingface.co/BlueZeros/MING-7B">MING-7B</a></center></td>
  </tr>

  <tr>
      <td><center>MING-1.8B</center></td>
      <td><center><a href="https://huggingface.co/Qwen/Qwen1.5-1.8B-Chat">Qwen1.5-1.8B</a></center></td>
      <td><center>🤗<a href="https://huggingface.co/BlueZeros/MING-1.8B">MING-1.8B</a></center></td>
  </tr>

  <tr>
      <td><center>MING-MOE-1.8B</center></td>
      <td><center><a href="https://huggingface.co/Qwen/Qwen1.5-1.8B-Chat">Qwen1.5-1.8B</a></center></td>
      <td><center>🤗<a href="https://huggingface.co/BlueZeros/MING-MOE-1.8B">MING-MOE-1.8B</a></center></td>
  </tr>

  <tr>
      <td><center>MING-MOE-4B</center></td>
      <td><center><a href="https://huggingface.co/Qwen/Qwen1.5-4B-Chat">Qwen1.5-4B</a></center></td>
      <td><center>🤗<a href="https://huggingface.co/BlueZeros/MING-MOE-4B">MING-MOE-4B</a></center></td>
  </tr>

  <tr>
      <td><center>MING-MOE-7B</center></td>
      <td><center><a href="https://huggingface.co/Qwen/Qwen1.5-7B-Chat">Qwen1.5-7B</a></center></td>
      <td><center>🤗<a href="https://huggingface.co/BlueZeros/MING-MOE-7B">MING-MOE-7B</a></center></td>
  </tr>

  <tr>
      <td><center>MING-MOE-14B</center></td>
      <td><center><a href="https://huggingface.co/Qwen/Qwen1.5-14B-Chat">Qwen1.5-14B</a></center></td>
      <td><center>🤗<a href="https://huggingface.co/BlueZeros/MING-MOE-14B">MING-MOE-14B</a></center></td>
  </tr>
</table>
</body>
</html>


## ⚡快速开始

1. 配置环境（测试环境如下，具体版本可以根据实际需求配置）

   * python==3.9.16
   * pytorch==2.0.1+cu117
   * peft==0.9.0

2. 安装项目依赖 

   ```bash
   git clone https://github.com/MediaBrain-SJTU/MING
   cd MING
   pip install -e .
   ```

2. 下载模型参数并运行（要求单卡显存 >= 15G）

   ```bash
   # MING-MOE
   CUDA_VISIBLE_DEVICES=0 python -m fastchat.serve.cli \
       --model_path {path_to_checkpoint} \ # 模型路径
       --model_base {path_to_base_model} \ # 基座模型路径
       --max-new-token 3072 # 输出最大长度

   # MING-1.8B
   CUDA_VISIBLE_DEVICES=0 python -m fastchat.serve.cli \
       --model_path {path_to_checkpoint} \ # 模型路径
       --max-new-token 2048 # 输出最大长度

   # MING-7B
   CUDA_VISIBLE_DEVICES=0 python -m fastchat.serve.cli \
       --model-path {path_to_checkpoint}  # 模型路径
       --max-new-token 512 # 输出最大长度
       --beam-size 3 # beam search宽度
       --temperature 1.2 # 采样温度
   ```
   
   * 注：由于transformers库的问题，当beam-size > 1时，需要满足temperature>=1.0，否则会报错。

4. 命令行运行实例

   * 对话支持多轮

   * 对话中输入关键词 `new chat` 能够开启新一轮对话。

     

## 🗃️数据集构建

数据集主要由四个部分构成：

<!DOCTYPE html>
<html>
<head>
</head>
<body>
<table style="width: 70%;">
  <tr>
      <td style="width: 20%;"><strong>数据类型</strong></td>
      <td style="width: 50%;"><strong>数据构成</strong></td>
      <td style="width: 10%;"><strong>数量</strong></td>
      <td style="width: 10%;"><strong>占比(%)</strong></td>
  </tr>
  <tr>
    <td rowspan="4">医疗知识问答</td>
    <td>基于临床指南和医疗共识的知识问答</td>
    <td>168k</td>
    <td rowspan="4">48.88</td>
  </tr>
  <tr>
    <td>基于医师资格考试题的知识问答</td>
    <td>77k</td>
  </tr>
  <tr>
    <td>真实医患问答</td>
    <td>140k</td>
  </tr>
  <tr>
    <td>基于结构化医疗图谱的知识问答</td>
    <td>160k</td>
  </tr>
  <tr>
    <td rowspan="3">多轮情景诊断与案例分析</td>
    <td>基于HealthCareMagic构造的多轮情景问答与诊断 </td>
    <td>200k</td>
    <td rowspan="3">21.52</td>
  </tr>
  <tr>
    <td>基于USMLE案例分析题的格式化多轮问诊</td>
    <td>20k</td>
  </tr>
  <tr>
    <td>多轮病人信息推理与诊断</td>
    <td>20k</td>
  </tr>
  <tr>
    <td rowspan="2">任务指令</td>
    <td>医疗指令</td>
    <td>150k</td>
    <td rowspan="2">26.91</td>
  </tr>
  <tr>
    <td>通用指令</td>
    <td>150k</td>
  </tr>
  <tr>
    <td rowspan="2">安全性数据</td>
    <td>敏感性问题</td>
    <td>15k</td>
    <td rowspan="2">2.69</td>
  </tr>
  <tr>
    <td>医疗反事实</td>
    <td>15k</td>
  </tr>
  <tr>
    <td><strong>总计</strong></td>
    <td>-</td>
    <td>1.12M</td>
    <td>100.00</td>
  </tr>
</table>
</body>
</html>


## 🧭测试样例

<details><summary><strong>体检报告分析</strong></summary>
<table style="width: 100%;">
  <tr>
      <td colspan="2"><strong>问题</strong></td>
  </tr>
  <tr>
      <td colspan="2">身高cm=‘null’, 体重kg=‘null’, bmi=‘null’, 收缩压=‘130’, 舒张压=‘75’, 高血压史=‘null’, 心率=‘84’, 糖尿病史=‘null’, 肝功能十项=‘白球比例 = [1.96]、总蛋白 = [74]、白蛋白 = [49]、前白蛋白 = [264]、总胆红素 = [11.6]、直接胆红素 = [2.4]、胆汁酸 = [2.3]、丙氨酸氨基转移酶 = [64]、天门冬氨酸氨基转移酶 = [30]、γ-谷氨酰基转移酶 = [65] ↑、碱性磷酸酶 = [80]’, 血脂四项=‘总胆固醇 = [5.08]、甘油三酯 = [1.75] ↑、高密度脂蛋白胆固醇 = [1.07]、低密度脂蛋白胆固醇 = [3.34]’, 甲状腺(FT3 FT4 TSH)=‘促甲状腺素(TSH) = [0.6415]、游离甲状腺素(FT4) = [12.67]、游离三碘甲腺原氨酸(FT3) = [4.98]’,空腹血糖=‘葡萄糖 = [5.35]’, 癌胚抗原=‘癌胚抗原 = [1.16]’, 甲胎蛋白=‘甲胎蛋白 = [4.68]’, ca199=‘糖类抗原199 = [3.1]’, ca125=‘糖类抗原125 = [5.5]’, ca153=‘null’, 肾功能三项=‘尿素 = [5.2]、肌酐 = [82]、尿酸 = [390]’, 血常规=‘嗜碱性粒细胞计数 = [0.00]、嗜碱性粒细胞% = [0.6]、嗜酸性粒细胞计数 = [0.10]、嗜酸性粒细胞% = [0.8]、红细胞比容 = [0.491]、血红蛋白 = [160]、淋巴细胞计数 = [2.50]、淋巴细胞% = [33.4]、平均血红蛋白量 = [28.5]、平均血红蛋白浓度 = [325]、平均红细胞体积 = [87.5]、单核细胞计数 = [0.60]、单核细胞% = [7.3]、血小板平均体积 = [8.3]、中性粒细胞计数 = [4.40]、中性粒细胞% = [57.9]、血小板计数 = [276]、红细胞计数 = [5.61]、红细胞分布宽度 = [13.2]、白细胞计数 = [7.60]’, 血沉=‘红细胞沉降率 = [1]’, 糖化血红蛋白=‘糖化血红蛋白(HbA1C) = [5.3]’, 尿常规=‘结晶(镜检) = [阴性(-)]、白细胞 = [阴性(-)]、比重 = [1.023]、酸碱度 = [5.0]、亚硝酸盐 = [阴性(-)]、蛋白质 = [阴性(-)]、酮体 = [阴性(-)]、尿胆元 = [阴性(-)]、胆红素 = [阴性(-)]、葡萄糖 = [阴性(-)]、潜血 = [弱阳性]、红细胞(镜检) = [0]、白细胞(镜检) = [0]、上皮细胞(镜检) = [0]、管型(镜检) = [0]、颜色 = [黄色]、清晰度 = [清晰]’, 粪常规+隐血=‘颜色 = [黄色]、性状 = [软便]、虫卵 = [阴性（-）]、红细胞 = [阴性（-）]、白细胞 = [阴性（-）]、隐血试验 = [阴性(-)]’, 内科=‘腹壁厚、心率[84]次/分’, 外科=‘肛拒检、颈部无明显异常’,血压=‘血压[130/75]mmHg’, 胸片(正侧)=‘影像表现：所示胸廓骨骼及胸壁软组织未见异常。纵隔及气管居中未见移位。纵隔未见增宽。心脏形态大小未见异常。两膈光整，两肋膈角锐利。肺门形态大小位置未见异常。两肺野清晰未见异常密度。请根据上述提供的体检指标作出分析及建议。</td>
  </tr>
  <tr>
      <td style="width: 50%;"><strong>ChatGPT</strong></td>
      <td style="width: 50%;"><strong>MING-7B</strong></td>
  </tr>
  <tr>
      <td><p>根据您提供的体检指标，我将对其中涉及的各项指标进行分析和建议：</p><p>血压：您的收缩压为130 mmHg，舒张压为75 mmHg，属于正常范围。维持血压在正常范围有助于心血管健康，建议保持健康的生活方式，如合理饮食、适量运动等。</p><p>血脂四项：总胆固醇为5.08 mmol/L，甘油三酯为1.75 mmol/L，高密度脂蛋白胆固醇为1.07 mmol/L，低密度脂蛋白胆固醇为3.34 mmol/L。甘油三酯稍微升高，建议控制饮食，减少高脂肪和高糖食物的摄入，增加锻炼，有助于调节血脂水平。<p>空腹血糖：葡萄糖水平为5.35 mmol/L，在正常范围内，但也建议保持健康的饮食和生活习惯，预防糖尿病的发生。</p><p>血常规：血红蛋白为160 g/L，红细胞计数为5.61 × 10^12/L，白细胞计数为7.60 × 10^9/L，血常规结果总体上看起来在正常范围内。</p><p>肝功能十项：各项指标在正常范围内，说明您的肝功能正常。</p><p>甲状腺功能：促甲状腺素(TSH)、游离甲状腺素(FT4)、游离三碘甲腺原氨酸(FT3)的水平也都在正常范围内。</p><p>尿常规：尿常规中有微弱的潜血阳性，这可能提示潜在的泌尿系统问题。建议您定期复查尿常规，如果有持续的异常，可以咨询医生进行进一步检查。</p><p>粪常规+隐血：粪便常规和隐血试验结果都在正常范围内，没有异常发现。</p><p>总体来说，您的体检结果在大部分项目上都表现为正常范围内。然而，血脂中甘油三酯稍有升高和尿常规中微弱的潜血阳性可能值得关注。在健康方面，建议您保持良好的饮食习惯、适量的体育锻炼，定期体检，如有其他疑虑或症状，最好咨询医生进行详细评估和建议。</p></td>
      <td><p>根据您提供的体检指标，我可以为您作出如下分析：</p><p>1. 身高、体重、BMI：没有提供相关的信息。</p><p>2. 血压：您的舒张压处于正常范围，而收缩压略高于正常值。建议您定期监测血压，如有需要请咨询医生。</p><p>3. 高血压史：您没有提及是否有高血压史，如果有请及时就医。</p><p>4. 心率：您的心率处于正常范围。</p><p>5. 糖尿病史：您没有提及是否有糖尿病史，如果有请及时就医。</p><p>6. 肝功能十项：您的肝功能十项指标中，白球比例、总蛋白、白蛋白、前白蛋白、总胆红素、直接胆红素、胆汁酸的值都在正常范围内，丙氨酸氨基转移酶和天门冬氨酸氨基转移酶的值稍高，但仍在正常范围内。</p><p>7. 血脂四项：您的总胆固醇和甘油三酯的值都高于正常范围，高密度脂蛋白胆固醇的值低于正常范围，低密度脂蛋白胆固醇的值接近正常范围。建议您控制饮食，适量运动，如有需要请咨询医生。</p><p>8. 甲状腺功能：您的促甲状腺素和游离三碘甲腺原氨酸的值都在正常范围内，游离甲状腺素的值稍高，但仍在正常范围内。</p><p>9. 血糖：您的空腹血糖处于正常范围，糖化血红蛋白的值也处于正常范围内。</p><p>10. 癌胚抗原、甲胎蛋白：您的癌胚抗原和甲胎蛋白的值都在正常范围内。</p><p>针对以上分析，建议您继续保持良好的生活习惯，注意饮食健康，适量运动，定期监测血压和血糖，如有需要请咨询医生。如果有其他问题，请随时向我咨询。</p></td>
  </tr>
</table>
</details>

<details><summary><strong>影像报告分析</strong></summary>
<table style="width: 100%;">
  <tr>
      <td colspan="2"><strong>问题</strong></td>
  </tr>
  <tr>
      <td colspan="2">能否用简单的语言解释一下这份检查报告存在哪些问题？我的妇科B超所见：双侧卵巢内见10多枚小卵泡回声；子宫直肠窝见少许液性暗区</td>
  </tr>
  <tr>
      <td style="width: 50%;"><strong>ChatGPT</strong></td>
      <td style="width: 50%;"><strong>MING-7B</strong></td>
  </tr>
  <tr>
      <td><p>当您的妇科B超检查报告提到"双侧卵巢内见10多枚小卵泡回声"和"子宫直肠窝见少许液性暗区"时，可能存在以下问题：</p><p>1. 多枚小卵泡回声：这意味着您的卵巢内有许多小的卵泡。在某些情况下，这可能是正常的，特别是在女性的排卵周期中，卵巢会发育多个卵泡，并最终释放一个卵子。然而，如果卵泡数量异常增多，可能会与多囊卵巢综合征等问题相关。</p><p>2. 液性暗区：这意味着在子宫直肠窝（子宫后方与直肠之间的区域）中存在一些液体。这个液体的原因可能是炎症、囊肿、或其他病变引起的。</p><p>需要强调的是，我并不是医生，无法对具体的病例进行诊断。要正确理解这份检查报告，最好的做法是咨询您的医生或专业医疗团队。他们可以根据您的个人情况，解释报告的含义，并提供必要的诊断和治疗建议。</p></td>
      <td><p>非常感谢您的咨询。根据您提供的检查报告，双侧卵巢内出现了多枚小卵泡回声，这可能是卵巢功能异常的表现。此外，子宫直肠窝也发现了少许液性暗区，这可能是子宫内膜异位症的表现。这些问题可能会影响您的生育能力，因此建议您及时就医，进行进一步的检查和治疗。</p><p>对于卵巢功能异常，我们通常会建议您进行促排卵治疗，以促进卵泡的发育和排卵。对于子宫内膜异位症，我们可以采用药物治疗或手术治疗，具体治疗方案需要根据您的具体情况而定。</p><p>此外，建议您定期进行妇科检查，保持良好的生活习惯，避免过度劳累和情绪波动，保持心情愉悦，有助于维护女性健康。</p><p>如果您还有其他问题或需要进一步的帮助，请随时与我们联系。祝您早日康复！</p></td>
  </tr>
</table>
</details>

<details><summary><strong>建议咨询</strong></summary>
<table style="width: 100%;">
  <tr>
      <td colspan="2"><strong>问题</strong></td>
  </tr>
  <tr>
      <td colspan="2">我母亲，60岁，体检时骨质疏松报告显示T值-3.5，Z值-2.1。饮食习惯：和家里的男性比起来吃肉不多，但和女性相比，量也正常。就诊记录：之前去当地医院就诊，医生建议要正规化治疗，多方面都要涉及。还说要打种什么针，一年几针的，具体记不清了。想咨询下医生：1. 像这个报告说的情况严重吗，我和我妈都挺担心的2. 正规化治疗，有哪些方面？3. 要打针的，是什么药？要住院吗？贵不贵？4. 这个病对生活影响大吗？5. 生活习惯方面有没有建议？尤其是她平常还做瑜伽，要不要紧？</td>
  </tr>
  <tr>
      <td style="width: 50%;"><strong>ChatGPT</strong></td>
      <td style="width: 50%;"><strong>MING-7B</strong></td>
  </tr>
  <tr>
      <td><p>我可以理解您和您母亲对这个情况的担忧。骨质疏松是一种常见的骨骼疾病，主要是骨密度降低，骨组织变得脆弱容易骨折。让我逐个回答您的问题：</p><p>1. 报告显示T值-3.5，Z值-2.1，这表明您母亲的骨质疏松程度较为严重。T值和Z值是用来衡量骨密度的标准，T值越低，表示骨密度距离年轻健康的标准值差距越大，而Z值是与同龄人相比较的标准。</p><p>2. 正规化治疗通常涉及多个方面，包括药物治疗、饮食调整、锻炼以及生活方式改变。药物治疗常用的包括：激素替代治疗、双磷酸盐、选择性雌激素受体调节剂等。但具体使用何种药物需要医生根据患者的情况来判断。</p><p>3. 关于药物治疗，医生可能会建议打激素类或者其他类的针剂，这些针剂通常是用来增加骨密度的。大部分情况下，这些针剂是通过皮下注射，而不是住院治疗。关于价格，具体药物的费用会因地区和医院的不同而异，建议您在咨询医生时详细了解费用情况。</p><p>4. 骨质疏松如果不得到有效治疗，可能会导致骨折的风险增加，尤其是髋部、脊椎等骨骼易受影响。这些骨折会给生活带来很大的影响，限制活动能力，甚至可能导致长期疼痛和功能障碍。</p><p>5. 生活习惯方面的建议包括增加钙和维生素D的摄入，这对于骨骼健康很重要。同时，规律的有氧锻炼、体重训练和平衡性锻炼对于预防骨质疏松和骨折风险的降低也很有帮助。至于瑜伽，很多瑜伽动作可以帮助增强肌肉力量和平衡性，但是建议在治疗方面请医生的意见，因为有些动作可能需要避免或调整。</p><p>总的来说，对于骨质疏松，早期发现和积极治疗是很重要的。建议您尽快带您的母亲去正规医院专科进行详细的诊断和治疗方案制定，以便及早控制疾病进展，减少骨折风险，并改善生活质量。</p></td>
      <td><p>您好，根据您提供的信息，您母亲的骨质疏松情况较为严重，T值-3.5和Z值-2.1表明她的骨密度明显低于正常人群。骨质疏松是一种常见的老年疾病，会导致骨质变薄、易碎，从而增加骨折的风险。</p><p>针对您的问题，我来逐一回答：</p><p>1. 这个报告的情况非常严重，您和您的母亲都应该非常担心。骨质疏松是一种慢性疾病，需要长期的治疗和管理。</p><p>2. 骨质疏松的正规化治疗包括药物治疗、营养补充和运动锻炼等多个方面。药物治疗主要是通过补充钙、维生素D和骨吸收抑制剂等药物来促进骨密度的增加。营养补充也很重要，建议增加摄入富含钙和维生素D的食物，如奶制品、豆制品、鱼类等。运动锻炼可以增强骨骼和肌肉的力量，减少骨折的风险。</p><p>3. 具体的药物治疗需要根据患者的具体情况来确定，一般包括钙剂、维生素D、双膦酸盐等药物。这些药物需要医生的指导和监督，一般不会住院，可以在门诊进行治疗。</p><p>4. 骨质疏松对生活有一定的影响，但通过合理的治疗和管理，可以减少骨折的风险，提高生活质量。</p><p>5. 生活习惯方面，建议您母亲避免长时间保持同一姿势，尤其是久坐或久站。可以适当增加户外活动时间，进行适量的有氧运动，如散步、慢跑等。此外，戒烟限酒，保持良好的心态和充足的睡眠也很重要。</p><p>最后，建议您母亲定期复查骨密度，根据医生的建议进行治疗和管理。如果有任何疑问或需要进一步的帮助，请及时咨询医生。祝您母亲早日康复！</p></td>
  </tr>
</table>
</details>




## 🪶贡献

本项目由上海交通大学未来媒体网络协同创新中心和上海人工智能实验室智慧医疗中心合作研发。模型数据系统主要由廖育生，孟昱同，刘泓呈完成，指导教师为[王钰](https://mediabrain.sjtu.edu.cn/yuwang/)副教授。



## 免责声明

预训练模型是基于大量语料库和算法模型进行训练的，并且在训练过程中可能存在偏差、错误和不完整的信息。因此，本项目提供的预训练模型仅供参考和研究使用，并不能保证其准确性和可靠性。使用预训练模型产生的结果可能存在误差和偏差，不能用于实际应用或决策。本项目不对使用预训练模型所产生的结果承担任何责任，也不对因使用预训练模型所产生的任何损失承担责任。使用者在使用预训练模型时应自行承担风险并进行自我验证。



## 引用

如果你使用了本项目的数据或者代码，请声明引用

```latex
@misc{MING,
  author={Yusheng Liao, Yutong Meng, Hongcheng Liu, Yu Wang, Yanfeng Wang},
  title = {明医 (MING)：中文医疗问诊大模型},
  year = {2023},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/MediaBrain-SJTU/MING}},
}
```

