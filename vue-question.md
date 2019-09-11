1. vue init webpack projectName 时报错：Error: EACCES: permission denied, unlink '/Users/connieqi/.vue-templates/webpack/.gitignore'

重复安装了vue cli解决了这个问题，应该时权限问题，下次尝试使用sudo ＋ 命令。

2、vue开发时调用线上接口，config/index.js内配置

proxyTable: {
        '/ucdisk': {
            target: 'http://192.168.12.100:8001/',//要访问的接口地址
            changeOrigin: true,
            pathRewrite: {
              '^/ucdisk': '/ucdisk'  //要拦截监听的内容
            }
        }
    },

axios.post('/ucdisk/api/2.0/user/login',Qs.stringify({
  			userName:this.username,
				passWord:this.password,
				clientKey:'0',
  		}))
      .then(this.getUserInfo)
      
这里需要注意一项内容，虽然配置生效了，但是通过浏览器F12查看调用的接口，仍然是本地的localhost或者本机IP地址，这里直接正常调用就行。。
另外，axios的参数需要引用qs（axios内置，无需单独安装），对参数执行stringify即可
