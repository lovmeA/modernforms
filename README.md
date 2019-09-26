# Modern Forms (精美的纯css3 html5表单框架) 验证器

#### 说明：
1. 标签属性
    1.  `data-required`: 普通文本必填项 `data-required="提示信息"`
    2.  `data-length`: 长度区间 `data-length="4-6"`
    3.  `data-length`: ~到无穷大 `data-length="100-*"`
    4.  `data-min`: 最小值 `data-min="5"`
    5.  `data-max`: 最大值 `data-min="10"`
    6.  `data-rules`: 自定义正则 `data-rules="/^(0\d{2,3}\d{7,8}|0\d{2,3}-)\d{7,8}$/" data-rule-message="错误信息"`
    7.  `data-equal`: 对比 `data-equal="#id"`
    8.  `data-idcard`: 身份证验证 `data-idcard="身份证号码不正确"`
    9.  `data-url`: URL验证 ` data-url="URL验证失败"`
    10. `data-email`: 邮箱验证 ` data-email="请输入正确的电子邮箱"`
    11. `data-phone`: 手机号验证 ` data-phone="请输入正确的手机号码"`
2. js参数解释
    1. `url`: 默认`form.action`
    2. `method`: 默认`POST`
    3. `submitBtn`: 提交表单触发事件元素(默认:`input:submit`)
    4. `async`: 默认为`true`(同步)
    5. `data`: 额外提交的数据,数据格式:`{k:'v','k1':'v1'}`
    6. `success`: 表单提交成功方法 `function(){}`
    7. `fail`: 表单提交失败方法 `function(){}`
    8. `sends`: 是否向后台提交数据,默认为 `true`
    
#### 示例 `from` HTML配置
```html
<form class="modern-forms" id="form" style="width:600px;margin:30px auto">
    <fieldset>
        <div class="form-row">
            <div class="col col-6">
                <div class="field-group">
                    <input type="text" name="required" data-required="提示信息" class="mdn-input" placeholder="非空验证">
                    <label class="mdn-label">非空验证</label>
                    <span class="mdn-bar"></span>
                </div>
            </div>
            <div class="col col-6">
                <div class="field-group prepend-icon">
                    <input type="text" name="name2" data-length="4-10" data-required="长度验证不能为空" class="mdn-input" placeholder="长度为：4-6个字符">
                    <label class="mdn-label">长度验证</label>
                    <span class="mdn-icon"><i class="fa fa-envelope"></i></span>
                    <span class="mdn-bar"></span>
                </div>
            </div>
        </div>
        <div class="form-row">
            <div class="col col-6">
                <div class="field-group prepend-icon">
                    <input type="text" name="name3" data-min="5" data-max="10" class="mdn-input" placeholder="最小/大值：5-10">
                    <label class="mdn-label">最小/最大值</label>
                    <span class="mdn-icon"><i class="fa fa-globe"></i></span>
                    <span class="mdn-bar"></span>
                </div>
            </div>
            <div class="col col-6">
                <div class="field-group">
                    <input type="text" name="name4"
                           data-rules="/^https?:\/\/[A-Za-z0-9]+\.[A-Za-z0-9]+[\/=\?%\-&_~`@[\]\':+!]*([^<>\'\'])*$/"
                           data-rule-message="URL验证失败" class="mdn-input" placeholder="自定义URL">
                    <label class="mdn-label">自定义URL</label>
                    <span class="mdn-bar"></span>
                </div>
            </div>
        </div>
        <div class="form-row">
            <div class="col col-6">
                <div class="field-group">
                    <input type="text" name="name5" data-length="6-16" id="name5" class="mdn-input" placeholder="输入相同">
                    <label class="mdn-label">输入相同</label>
                    <span class="mdn-bar"></span>
                </div>
            </div>
            <div class="col col-6">
                <div class="field-group">
                    <input type="text" name="name6" data-equal="#name5" class="mdn-input" placeholder="输入相同">
                    <label class="mdn-label">输入相同</label>
                    <span class="mdn-bar"></span>
                </div>
            </div>
        </div>
        <div class="form-row">
            <div class="col col-6">
                <div class="field-group">
                    <input type="url" name="name7" data-url="URL验证失败" class="mdn-input" placeholder="URL验证">
                    <label class="mdn-label">URL验证</label>
                    <span class="mdn-bar"></span>
                </div>
            </div>
            <div class="col col-6">
                <div class="field-group">
                    <input type="text" name="name8" data-required="身份证号码不能为空" data-idcard="身份证号码不正确" class="mdn-input" placeholder="身份证号码">
                    <label class="mdn-label">身份证号码</label>
                    <span class="mdn-bar"></span>
                </div>
            </div>
        </div>
        <div class="form-row">
            <div class="field-group">
                <input type="email" name="email9" data-email="请输入正确的电子邮箱" data-required="邮箱不能为空" class="mdn-input" placeholder="电子邮箱">
                <label class="mdn-label">电子邮箱</label>
                <span class="mdn-bar"></span>
            </div>
        </div>
        <div class="form-row">
            <div class="field-group prepend-icon">
                <input type="text" name="name10" data-phone="请输入正确的手机号码" data-required="手机号码不能为空" class="mdn-input" placeholder="手机号码">
                <label class="mdn-label">手机号码</label>
                <span class="mdn-icon"><i class="fa fa-globe"></i></span>
                <span class="mdn-bar"></span>
            </div>
        </div>
    </fieldset>
    <div class="mdn-footer">
        <button type="button" id="submitBtn" class="mdn-button btn-primary">提交</button>
    </div>
</form>
```
    
#### 示例 `from` JQuery配置

```javascript
$('#form').form({
    url: '/url',
    method: 'POST',
    submitBtn: '#submitBtn',
    async: true,
    sends: true,
    data: {
        data1: 'value1',
        data2: 'value2',
        data3: 'value3'
    },
    success: function (data) {
        console.log(data)
    },
    fail: function (data) {
        console.log(data)
    }
});
```