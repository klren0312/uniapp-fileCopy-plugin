# 文件复制插件
### 使用方法
1. 若想复制任意目录, 则需要配置`manifest.json`
```json
"permissionExternalStorage" : {
	//可选，JSON对象，Android平台应用启动时申请读写手机存储权限策略
	"request" : "always", //必填，字符串类型，申请读写手机存储权限策略，可取值none、once、always
	"prompt" : "应用更新和下载文件，需要获取读写手机存储（系统提示为访问设备上的照片、媒体内容和文件）权限，请允许。" //可选，字符串类型，当request设置为always值用户拒绝时弹出提示框上的内容
},
```

2. 使用示例
```vue
<template>
	<view>
		<button @click="utsCopyFile">uts复制文件</button>
	</view>
</template>

<script>
	import * as ZZESFileCopy from '../../uni_modules/zzes-filecopy'
	export default {
		methods: {
			utsCopyFile() {
				const File = plus.android.importClass('java.io.File')
				const publicDir = new File(Environment.getExternalStorageDirectory(), 'Download').getAbsolutePath()
				const res = ZZESFileCopy.doCopyFile(publicDir + '/test.pdf', publicDir + '/test/',  'test.pdf')
				console.log(res)
			},
		}
	}
</script>

```

### 开发文档
[UTS 语法](https://uniapp.dcloud.net.cn/tutorial/syntax-uts.html)
[UTS 原生插件](https://uniapp.dcloud.net.cn/plugin/uts-plugin.html)
[Hello UTS](https://gitcode.net/dcloud/hello-uts/-/tree/dev)