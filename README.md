# BatOpenAPI
宝安通开放接口

使用方式

一、准备工作

1.添加Gradle依赖
<pre>
	dependencies{
   		 compile 'com.hxsoft.bat.openapi:bat-open-api:3.1.0'
	}
 </pre>	
二、使用方式
<pre>
	//获取一个api实例
	BatOpenApi batOpenApi = APIInvoke.getApi();
	//a.人脸核身
	batOpenApi.faceRecognition(context, name, id, token, new DefaultActionListener<String>() {
		@Override
		public void onSuccess(String o) {
		   //人脸核身成功
		}
		@Override
		public void onFailure(int errCode, String errMsg, Throwable t) {
			//人脸核身失败
			Toast.makeText(CloudFaceActivity.this, errMsg, Toast.LENGTH_LONG).show();
		}
	});
	 // b.语音 
	 openApi.speechDialog(this, new DefaultActionListener<String>() {
		@Override
		public void onSuccess(String s) {
		   //语音转换为文字
		}
		@Override
		public void onFailure(int errCode, String errMsg, Throwable t) {

		}
	});
	// c.二唯码扫描
	openApi.scan(this, 11);
	@Override
	public void onActivityResult(int requestCode, int resultCode, Intent data) {
		super.onActivityResult(requestCode, resultCode, data);
		if (resultCode == RESULT_OK) {
		   if(requestCode == 11){
				String result = data.getStringExtra("result");
			}
		} 
	}
	// d.获取用户信息
	UserInfo userInfo = openApi.getUserInfo();
	// e.打开客服界面（"模块名称", "事项名称", "部门名称"可为空）
	openApi.contactCustomer(context,"模块名称", "事项名称", "部门名称");
	// f.进入宝安通登录界面
	openApi.toLoginView(activity,12);
	@Override
	public void onActivityResult(int requestCode, int resultCode, Intent data) {
		super.onActivityResult(requestCode, resultCode, data);
		if (resultCode == 1) {
		   if(requestCode == 12){
				// login success!
			}
		} 
	}
</pre>
    
