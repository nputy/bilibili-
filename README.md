Bilibili 评论数据集（BLBL-Comment-Dataset）
数据集简介
本数据集包含 B 站多视频的用户评论及关联信息，每条视频对应独立文件夹，内含评论数据、视频元信息等文件，可用于社交网络分析、情感分析、用户行为研究等学术任务。
数据集结构
根目录结构
以视频 BV 号为文件夹名，示例：
plaintext
BLBL-Comment-Dataset/
├── BV1A2hXzDEnW_探秘废弃的河南省会，这里还剩啥？【地球知识局】/
├── BV1A4sJBcEXM_Dory | 坐在地暖上喝冰啤酒.../
├── BV1a4wBceBz_【第234期】《南海归旧属问题.../
└── ...（更多视频文件夹）
单视频文件夹内容
每个视频文件夹包含以下文件：
表格
文件名	类型	说明
BVxxxx.csv	CSV 文件	该视频的用户评论数据（含用户信息、评论内容、互动数据等）
BVxxxx.geojson	GEOJSON 文件	评论用户地理位置关联数据（部分视频包含）
BVxxxx.html	HTML 文件	评论区原始网页快照（数据溯源用）
video_info.json	JSON 文件	视频元信息（BV 号、标题、UP 主、评论总数等）
评论数据字段说明（CSV 文件）
表格
字段名	类型	说明
bvid	字符串	视频 BV 号
upname	字符串	评论用户昵称
sex	字符串	用户性别（男 / 女 / 保密）
content	字符串	评论内容
like	整数	评论获赞数
location	字符串	用户地理位置
level	整数	用户 B 站等级
ctime	整数	评论发布时间戳（毫秒级）
视频元信息示例（video_info.json）
json
{
  "bvid": "BV1A2hXzDEnW",
  "aid": "115111331170360",
  "title": "探秘废弃的河南省会，这里还剩啥？【地球知识局】",
  "author": "地球知识局",
  "comment_count": 1146
}
数据来源与声明
数据采集自 B 站公开视频评论区，仅用于学术研究与非商业用途，使用需遵守 B 站用户协议及相关法律法规。
使用示例（Python）
python
运行
import pandas as pd
# 读取某视频评论数据
df = pd.read_csv("BV1A2hXzDEnW/BV1A2hXzDEnW.csv")
print(df.head())
