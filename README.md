#  jQuery Validation筆記   

這個針對簡單的網站真的不用寫一大堆未來難管理的驗證

```
<script src="/js/jquery.min.js"></script>
<script src="/js/jquery.validate.min.js"></script>

<script>

  //在jQuery Validation中加入自訂規則isMultiple100(100的倍數)
  jQuery.validator.addMethod("isMultiple100", function(value, element) {
      if(value) {
          return value%100==0; // 輸入內容中不可有空白字元
      } else {
          return false;
      }
  });

  $().ready(function () {
    $("#Form1").validate({
        rules: {
            merOrdAmt: {
                required: true,
                digits: true,
                min:100,
                max:10000,
                isMultiple100:true
            }
        }, messages: {
            merOrdAmt: {
                required: "请输入金额",
                digits: "请输入数字",
                min:"金额最低100元",
                max:"金额最高10000元",
                isMultiple100:"请输入100的倍数"
            },
            BankCode :{
                required: "请选择银行"
            },
            CHANNELCODE:{
                required: "请选择支付"
            }
        }
    });
  });
</script>


<!--DIV-->
<div id="PayDiv" class="panel panel-default PayDiv" style="display: none;">
    <div class="panel-body">
        <form id="Form1" action="#" method="post" target="_blank">
            <input type="hidden" name="payType" value="交易種類">
            <div class="form-group">
                <label for="merOrdAmt">訂單金额<font color="red">(最低金额100、最高金额5000、金额需要為100的倍数)</font></label>
                <input type="number" class="form-control" name="merOrdAmt">
            </div>
            <div class="form-group">
                <label for="remark">備註</label>
                <input type="text" class="form-control" name="remark">
            </div>
            <div class="form-group">
                <button type="submit" class="btn btn-danger pay_btn">確認</button>
            </div>
        </form>
    </div>
</div>

```