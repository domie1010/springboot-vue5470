<template>
    <div class="addEdit-block">
        <el-form
                class="detail-form-content"
                ref="ruleForm"
                :model="ruleForm"
                :rules="rules"
                label-width="auto"
                >
            <el-row>
                <el-col :span="12"  v-if="sessionTable !='gongyingshang'">
                    <el-form-item class="select" v-if="type!='info'"  label="供应商信息" prop="gongyingshangId">
                        <el-select v-model="ruleForm.gongyingshangId" :disabled="ro.gongyingshangId" filterable placeholder="请选择供应商信息" @change="gongyingshangChange">
                            <el-option
                                    v-for="(item,index) in gongyingshangOptions"
                                    v-bind:key="item.id"
                                    :label="item.gongyingshangName"
                                    :value="item.id">
                            </el-option>
                        </el-select>
                    </el-form-item>
                </el-col>

                <el-col :span="12"  v-if="sessionTable !='gongyingshang' ">
                    <el-form-item class="input" v-if="type!='info'"  label="供应商名称" prop="gongyingshangName">
                        <el-input v-model="gongyingshangForm.gongyingshangName"
                                  placeholder="供应商名称" clearable readonly></el-input>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="供应商名称" prop="gongyingshangName">
                            <el-input v-model="ruleForm.gongyingshangName"
                                      placeholder="供应商名称" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
                <el-col :span="12"  v-if="sessionTable !='gongyingshang' ">
                    <el-form-item class="input" v-if="type!='info'"  label="联系人姓名" prop="lianxirenName">
                        <el-input v-model="gongyingshangForm.lianxirenName"
                                  placeholder="联系人姓名" clearable readonly></el-input>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="联系人姓名" prop="lianxirenName">
                            <el-input v-model="ruleForm.lianxirenName"
                                      placeholder="联系人姓名" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
                <el-col :span="12"  v-if="sessionTable !='gongyingshang' ">
                    <el-form-item class="input" v-if="type!='info'"  label="联系人手机号" prop="lianxirenPhone">
                        <el-input v-model="gongyingshangForm.lianxirenPhone"
                                  placeholder="联系人手机号" clearable readonly></el-input>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="联系人手机号" prop="lianxirenPhone">
                            <el-input v-model="ruleForm.lianxirenPhone"
                                      placeholder="联系人手机号" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
                <el-col :span="12"  v-if="sessionTable !='gongyingshang' ">
                    <el-form-item class="input" v-if="type!='info'"  label="地址" prop="lianxirenAddress">
                        <el-input v-model="gongyingshangForm.lianxirenAddress"
                                  placeholder="地址" clearable readonly></el-input>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="地址" prop="lianxirenAddress">
                            <el-input v-model="ruleForm.lianxirenAddress"
                                      placeholder="地址" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
                <el-col :span="12"  v-if="sessionTable !='gongyingshang' ">
                    <el-form-item class="input" v-if="type!='info'"  label="供应商类型" prop="gongyingshangValue">
                        <el-input v-model="gongyingshangForm.gongyingshangValue"
                                  placeholder="供应商类型" clearable readonly></el-input>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="供应商类型" prop="gongyingshangValue">
                            <el-input v-model="ruleForm.gongyingshangValue"
                                      placeholder="供应商类型" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
                <el-col :span="12"  v-if="sessionTable !='gongyingshang' ">
                    <el-form-item class="input" v-if="type!='info'"  label="信用等级" prop="gongyingshangXinyongdengjiValue">
                        <el-input v-model="gongyingshangForm.gongyingshangXinyongdengjiValue"
                                  placeholder="信用等级" clearable readonly></el-input>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="信用等级" prop="gongyingshangXinyongdengjiValue">
                            <el-input v-model="ruleForm.gongyingshangXinyongdengjiValue"
                                      placeholder="信用等级" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
                <input id="updateId" name="id" type="hidden">
            <input id="gongyingshangId" name="gongyingshangId" type="hidden">
               <el-col :span="12">
                   <el-form-item class="input" v-if="type!='info'"  label="物资名称" prop="wuziName">
                       <el-input v-model="ruleForm.wuziName"
                                 placeholder="物资名称" clearable  :readonly="ro.wuziName"></el-input>
                   </el-form-item>
                   <div v-else-if="type=='info'">
                       <el-form-item class="input" label="物资名称" prop="wuziName">
                           <el-input v-model="ruleForm.wuziName"
                                     placeholder="物资名称" readonly></el-input>
                       </el-form-item>
                   </div>
               </el-col>
               <el-col :span="12">
                   <el-form-item class="input" v-if="type!='info'"  label="物资编号" prop="wuziUuidNumber">
                       <el-input v-model="ruleForm.wuziUuidNumber"
                                 placeholder="物资编号" clearable  :readonly="ro.wuziUuidNumber"></el-input>
                   </el-form-item>
                   <div v-else-if="type=='info'">
                       <el-form-item class="input" label="物资编号" prop="wuziUuidNumber">
                           <el-input v-model="ruleForm.wuziUuidNumber"
                                     placeholder="物资编号" readonly></el-input>
                       </el-form-item>
                   </div>
               </el-col>
               <el-col :span="12">
                   <el-form-item class="input" v-if="type!='info'"  label="领取地点" prop="wuziAddress">
                       <el-input v-model="ruleForm.wuziAddress"
                                 placeholder="领取地点" clearable  :readonly="ro.wuziAddress"></el-input>
                   </el-form-item>
                   <div v-else-if="type=='info'">
                       <el-form-item class="input" label="领取地点" prop="wuziAddress">
                           <el-input v-model="ruleForm.wuziAddress"
                                     placeholder="领取地点" readonly></el-input>
                       </el-form-item>
                   </div>
               </el-col>
                <el-col :span="12">
                    <el-form-item class="upload" v-if="type!='info' && !ro.wuziPhoto" label="物资照片" prop="wuziPhoto">
                        <file-upload
                            tip="点击上传物资照片"
                            action="file/upload"
                            :limit="3"
                            :multiple="true"
                            :fileUrls="ruleForm.wuziPhoto?$base.url+ruleForm.wuziPhoto:''"
                            @change="wuziPhotoUploadChange"
                        ></file-upload>
                    </el-form-item>
                    <div v-else>
                        <el-form-item v-if="ruleForm.wuziPhoto" label="物资照片" prop="wuziPhoto">
                            <img style="margin-right:20px;" v-bind:key="index" v-for="(item,index) in (ruleForm.wuziPhoto || '').split(',')" :src="$base.url+item" width="100" height="100">
                        </el-form-item>
                    </div>
                </el-col>
               <el-col :span="12">
                   <el-form-item class="input" v-if="type!='info'"  label="物资型号" prop="wuziXinghao">
                       <el-input v-model="ruleForm.wuziXinghao"
                                 placeholder="物资型号" clearable  :readonly="ro.wuziXinghao"></el-input>
                   </el-form-item>
                   <div v-else-if="type=='info'">
                       <el-form-item class="input" label="物资型号" prop="wuziXinghao">
                           <el-input v-model="ruleForm.wuziXinghao"
                                     placeholder="物资型号" readonly></el-input>
                       </el-form-item>
                   </div>
               </el-col>
               <el-col :span="12">
                   <el-form-item class="input" v-if="type!='info'"  label="物资规格" prop="wuziGuige">
                       <el-input v-model="ruleForm.wuziGuige"
                                 placeholder="物资规格" clearable  :readonly="ro.wuziGuige"></el-input>
                   </el-form-item>
                   <div v-else-if="type=='info'">
                       <el-form-item class="input" label="物资规格" prop="wuziGuige">
                           <el-input v-model="ruleForm.wuziGuige"
                                     placeholder="物资规格" readonly></el-input>
                       </el-form-item>
                   </div>
               </el-col>
               <el-col :span="12">
                   <el-form-item class="input" v-if="type!='info'"  label="物资生产厂家" prop="wuziChangjia">
                       <el-input v-model="ruleForm.wuziChangjia"
                                 placeholder="物资生产厂家" clearable  :readonly="ro.wuziChangjia"></el-input>
                   </el-form-item>
                   <div v-else-if="type=='info'">
                       <el-form-item class="input" label="物资生产厂家" prop="wuziChangjia">
                           <el-input v-model="ruleForm.wuziChangjia"
                                     placeholder="物资生产厂家" readonly></el-input>
                       </el-form-item>
                   </div>
               </el-col>
                <el-col :span="12">
                    <el-form-item class="select" v-if="type!='info'"  label="物资类型" prop="wuziTypes">
                        <el-select v-model="ruleForm.wuziTypes" :disabled="ro.wuziTypes" placeholder="请选择物资类型">
                            <el-option
                                v-for="(item,index) in wuziTypesOptions"
                                v-bind:key="item.codeIndex"
                                :label="item.indexName"
                                :value="item.codeIndex">
                            </el-option>
                        </el-select>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item class="input" label="物资类型" prop="wuziValue">
                        <el-input v-model="ruleForm.wuziValue"
                            placeholder="物资类型" readonly></el-input>
                        </el-form-item>
                    </div>
                </el-col>
               <el-col :span="12">
                   <el-form-item class="input" v-if="type!='info'"  label="物资库存" prop="wuziKucunNumber">
                       <el-input v-model="ruleForm.wuziKucunNumber"
                                 placeholder="物资库存" clearable  :readonly="ro.wuziKucunNumber"></el-input>
                   </el-form-item>
                   <div v-else-if="type=='info'">
                       <el-form-item class="input" label="物资库存" prop="wuziKucunNumber">
                           <el-input v-model="ruleForm.wuziKucunNumber"
                                     placeholder="物资库存" readonly></el-input>
                       </el-form-item>
                   </div>
               </el-col>
               <el-col :span="12">
                   <el-form-item class="input" v-if="type!='info'"  label="价格" prop="wuziNewMoney">
                       <el-input v-model="ruleForm.wuziNewMoney"
                                 placeholder="价格" clearable  :readonly="ro.wuziNewMoney"></el-input>
                   </el-form-item>
                   <div v-else-if="type=='info'">
                       <el-form-item class="input" label="价格" prop="wuziNewMoney">
                           <el-input v-model="ruleForm.wuziNewMoney"
                                     placeholder="价格" readonly></el-input>
                       </el-form-item>
                   </div>
               </el-col>
                <el-col :span="24">
                    <el-form-item v-if="type!='info'"  label="物资介绍" prop="wuziContent">
                        <editor style="min-width: 200px; max-width: 600px;"
                                v-model="ruleForm.wuziContent"
                                class="editor"
                                action="file/upload">
                        </editor>
                    </el-form-item>
                    <div v-else-if="type=='info'">
                        <el-form-item v-if="ruleForm.wuziContent" label="物资介绍" prop="wuziContent">
                            <span v-html="ruleForm.wuziContent"></span>
                        </el-form-item>
                    </div>
                </el-col>
            </el-row>
            <el-form-item class="btn">
                <el-button v-if="type!='info'" type="primary" class="btn-success" @click="onSubmit">提交</el-button>
                <el-button v-if="type!='info'" class="btn-close" @click="back()">取消</el-button>
                <el-button v-if="type=='info'" class="btn-close" @click="back()">返回</el-button>
            </el-form-item>
        </el-form>
    </div>
</template>
<script>
    import styleJs from "../../../utils/style.js";
    // 数字，邮件，手机，url，身份证校验
    import { isNumber,isIntNumer,isEmail,isPhone, isMobile,isURL,checkIdCard } from "@/utils/validate";
    import utilsJs, {getYearFormat,getMonthFormat,getDateFormat,getDatetimeFormat} from "../../../utils/utils.js";
    export default {
        data() {
            return {
                addEditForm:null,
                id: '',
                type: '',
                sessionTable : "",//登录账户所在表名
                role : "",//权限
                userId:"",//当前登录人的id
                gongyingshangForm: {},
                ro:{
                    gongyingshangId: false,
                    wuziName: false,
                    wuziUuidNumber: false,
                    wuziAddress: false,
                    wuziPhoto: false,
                    wuziXinghao: false,
                    wuziGuige: false,
                    wuziChangjia: false,
                    wuziTypes: false,
                    wuziKucunNumber: false,
                    wuziNewMoney: false,
                    wuziContent: false,
                    wuziDelete: false,
                    insertTime: false,
                },
                ruleForm: {
                    gongyingshangId: '',
                    wuziName: '',
                    wuziUuidNumber: new Date().getTime(),
                    wuziAddress: '',
                    wuziPhoto: '',
                    wuziXinghao: '',
                    wuziGuige: '',
                    wuziChangjia: '',
                    wuziTypes: '',
                    wuziKucunNumber: '',
                    wuziNewMoney: '',
                    wuziContent: '',
                    wuziDelete: '',
                    insertTime: '',
                },
                wuziTypesOptions : [],
                gongyingshangOptions : [],
                rules: {
                   gongyingshangId: [
                              { required: true, message: '供应商不能为空', trigger: 'blur' },
                              {  pattern: /^[0-9]*$/,
                                  message: '只允许输入整数',
                                  trigger: 'blur'
                              }
                          ],
                   wuziName: [
                              { required: true, message: '物资名称不能为空', trigger: 'blur' },
                          ],
                   wuziUuidNumber: [
                              { required: true, message: '物资编号不能为空', trigger: 'blur' },
                          ],
                   wuziAddress: [
                              { required: true, message: '领取地点不能为空', trigger: 'blur' },
                          ],
                   wuziPhoto: [
                              { required: true, message: '物资照片不能为空', trigger: 'blur' },
                          ],
                   wuziXinghao: [
                              { required: true, message: '物资型号不能为空', trigger: 'blur' },
                          ],
                   wuziGuige: [
                              { required: true, message: '物资规格不能为空', trigger: 'blur' },
                          ],
                   wuziChangjia: [
                              { required: true, message: '物资生产厂家不能为空', trigger: 'blur' },
                          ],
                   wuziTypes: [
                              { required: true, message: '物资类型不能为空', trigger: 'blur' },
                              {  pattern: /^[0-9]*$/,
                                  message: '只允许输入整数',
                                  trigger: 'blur'
                              }
                          ],
                   wuziKucunNumber: [
                              { required: true, message: '物资库存不能为空', trigger: 'blur' },
                              {  pattern: /^[0-9]*$/,
                                  message: '只允许输入整数',
                                  trigger: 'blur'
                              }
                          ],
                   wuziNewMoney: [
                              { required: true, message: '价格不能为空', trigger: 'blur' },
                              {  pattern: /^[0-9]{0,6}(\.[0-9]{1,2})?$/,
                                  message: '只允许输入整数6位,小数2位的数字',
                                  trigger: 'blur'
                              }
                          ],
                   wuziContent: [
                              { required: true, message: '物资介绍不能为空', trigger: 'blur' },
                          ],
                   wuziDelete: [
                              { required: true, message: '逻辑删除不能为空', trigger: 'blur' },
                              {  pattern: /^[0-9]*$/,
                                  message: '只允许输入整数',
                                  trigger: 'blur'
                              }
                          ],
                   insertTime: [
                              { required: true, message: '录入时间不能为空', trigger: 'blur' },
                          ],
                }
            };
        },
        props: ["parent"],
        computed: {
        },
        created() {
            //获取当前登录用户的信息
            this.sessionTable = this.$storage.get("sessionTable");
            this.role = this.$storage.get("role");
            this.userId = this.$storage.get("userId");


            if (this.role != "管理员"){
            }
            this.addEditForm = styleJs.addStyle();
            this.addEditStyleChange()
            this.addEditUploadStyleChange()
            //获取下拉框信息
                this.$http({
                    url:`dictionary/page?page=1&limit=100&sort=&order=&dicCode=wuzi_types`,
                    method: "get"
                }).then(({ data }) => {
                    if (data && data.code === 0) {
                        this.wuziTypesOptions = data.data.list;
                    }
                });

         this.$http({
             url: `gongyingshang/page?page=1&limit=100`,
             method: "get"
         }).then(({ data }) => {
             if (data && data.code === 0) {
                this.gongyingshangOptions = data.data.list;
            }
         });

        },
        mounted() {
        },
        methods: {
            // 下载
            download(file){
                window.open(`${file}`)
            },
            // 初始化
            init(id,type) {
                if (id) {
                    this.id = id;
                    this.type = type;
                }
                if(this.type=='info'||this.type=='else'){
                    this.info(id);
                }
                // 获取用户信息
                this.$http({
                    url:`${this.$storage.get("sessionTable")}/session`,
                    method: "get"
                }).then(({ data }) => {
                    if (data && data.code === 0) {
                        var json = data.data;
                    } else {
                        this.$message.error(data.msg);
                    }
                });
            },
            gongyingshangChange(id){
                this.$http({
                    url: `gongyingshang/info/`+id,
                    method: "get"
                }).then(({ data }) => {
                    if (data && data.code === 0) {
                        this.gongyingshangForm = data.data;
                    }
                });
            },
            // 多级联动参数
            info(id) {
                let _this =this;
                _this.$http({
                    url: `wuzi/info/${id}`,
                    method: 'get'
                }).then(({ data }) => {
                    if (data && data.code === 0) {
                        _this.ruleForm = data.data;
                        _this.gongyingshangChange(data.data.gongyingshangId)
                        _this.ruleForm.wuziContent = _this.ruleForm.wuziContent.replaceAll("src=\"upload/","src=\""+this.$base.url+"upload/");
                    } else {
                        _this.$message.error(data.msg);
                    }
                });
            },
            // 提交
            onSubmit() {
                this.$refs["ruleForm"].validate(valid => {
                    if (valid) {
                        this.ruleForm.wuziContent = this.ruleForm.wuziContent.replaceAll(this.$base.url,"");
                        this.$http({
                            url:`wuzi/${!this.ruleForm.id ? "save" : "update"}`,
                            method: "post",
                            data: this.ruleForm
                        }).then(({ data }) => {
                            if (data && data.code === 0) {
                                this.$message({
                                    message: "操作成功",
                                    type: "success",
                                    duration: 1500,
                                    onClose: () => {
                                        this.parent.showFlag = true;
                                        this.parent.addOrUpdateFlag = false;
                                        this.parent.wuziCrossAddOrUpdateFlag = false;
                                        this.parent.search();
                                        this.parent.contentStyleChange();
                                    }
                                });
                            } else {
                                this.$message.error(data.msg);
                            }
                        });
                    }
                });
            },
            // 获取uuid
            getUUID () {
                return new Date().getTime();
            },
            // 返回
            back() {
                this.parent.showFlag = true;
                this.parent.addOrUpdateFlag = false;
                this.parent.wuziCrossAddOrUpdateFlag = false;
                this.parent.contentStyleChange();
            },
            //图片
            wuziPhotoUploadChange(fileUrls){
                this.ruleForm.wuziPhoto = fileUrls;
                this.addEditUploadStyleChange()
            },

            addEditStyleChange() {
                this.$nextTick(()=>{
                    // input
                    document.querySelectorAll('.addEdit-block .input .el-input__inner').forEach(el=>{
                        el.style.height = this.addEditForm.inputHeight
                        el.style.color = this.addEditForm.inputFontColor
                        el.style.fontSize = this.addEditForm.inputFontSize
                        el.style.borderWidth = this.addEditForm.inputBorderWidth
                        el.style.borderStyle = this.addEditForm.inputBorderStyle
                        el.style.borderColor = this.addEditForm.inputBorderColor
                        el.style.borderRadius = this.addEditForm.inputBorderRadius
                        el.style.backgroundColor = this.addEditForm.inputBgColor
                    })
                    document.querySelectorAll('.addEdit-block .input .el-form-item__label').forEach(el=>{
                        el.style.lineHeight = this.addEditForm.inputHeight
                        el.style.color = this.addEditForm.inputLableColor
                        el.style.fontSize = this.addEditForm.inputLableFontSize
                    })
                    // select
                    document.querySelectorAll('.addEdit-block .select .el-input__inner').forEach(el=>{
                        el.style.height = this.addEditForm.selectHeight
                        el.style.color = this.addEditForm.selectFontColor
                        el.style.fontSize = this.addEditForm.selectFontSize
                        el.style.borderWidth = this.addEditForm.selectBorderWidth
                        el.style.borderStyle = this.addEditForm.selectBorderStyle
                        el.style.borderColor = this.addEditForm.selectBorderColor
                        el.style.borderRadius = this.addEditForm.selectBorderRadius
                        el.style.backgroundColor = this.addEditForm.selectBgColor
                    })
                    document.querySelectorAll('.addEdit-block .select .el-form-item__label').forEach(el=>{
                        el.style.lineHeight = this.addEditForm.selectHeight
                        el.style.color = this.addEditForm.selectLableColor
                        el.style.fontSize = this.addEditForm.selectLableFontSize
                    })
                    document.querySelectorAll('.addEdit-block .select .el-select__caret').forEach(el=>{
                        el.style.color = this.addEditForm.selectIconFontColor
                        el.style.fontSize = this.addEditForm.selectIconFontSize
                    })
                    // date
                    document.querySelectorAll('.addEdit-block .date .el-input__inner').forEach(el=>{
                        el.style.height = this.addEditForm.dateHeight
                        el.style.color = this.addEditForm.dateFontColor
                        el.style.fontSize = this.addEditForm.dateFontSize
                        el.style.borderWidth = this.addEditForm.dateBorderWidth
                        el.style.borderStyle = this.addEditForm.dateBorderStyle
                        el.style.borderColor = this.addEditForm.dateBorderColor
                        el.style.borderRadius = this.addEditForm.dateBorderRadius
                        el.style.backgroundColor = this.addEditForm.dateBgColor
                    })
                    document.querySelectorAll('.addEdit-block .date .el-form-item__label').forEach(el=>{
                        el.style.lineHeight = this.addEditForm.dateHeight
                        el.style.color = this.addEditForm.dateLableColor
                        el.style.fontSize = this.addEditForm.dateLableFontSize
                    })
                    document.querySelectorAll('.addEdit-block .date .el-input__icon').forEach(el=>{
                        el.style.color = this.addEditForm.dateIconFontColor
                        el.style.fontSize = this.addEditForm.dateIconFontSize
                        el.style.lineHeight = this.addEditForm.dateHeight
                    })
                    // upload
                    let iconLineHeight = parseInt(this.addEditForm.uploadHeight) - parseInt(this.addEditForm.uploadBorderWidth) * 2 + 'px'
                    document.querySelectorAll('.addEdit-block .upload .el-upload--picture-card').forEach(el=>{
                        el.style.width = this.addEditForm.uploadHeight
                        el.style.height = this.addEditForm.uploadHeight
                        el.style.borderWidth = this.addEditForm.uploadBorderWidth
                        el.style.borderStyle = this.addEditForm.uploadBorderStyle
                        el.style.borderColor = this.addEditForm.uploadBorderColor
                        el.style.borderRadius = this.addEditForm.uploadBorderRadius
                        el.style.backgroundColor = this.addEditForm.uploadBgColor
                    })
                    document.querySelectorAll('.addEdit-block .upload .el-form-item__label').forEach(el=>{
                        el.style.lineHeight = this.addEditForm.uploadHeight
                        el.style.color = this.addEditForm.uploadLableColor
                        el.style.fontSize = this.addEditForm.uploadLableFontSize
                    })
                    document.querySelectorAll('.addEdit-block .upload .el-icon-plus').forEach(el=>{
                        el.style.color = this.addEditForm.uploadIconFontColor
                        el.style.fontSize = this.addEditForm.uploadIconFontSize
                        el.style.lineHeight = iconLineHeight
                        el.style.display = 'block'
                    })
                    // 多文本输入框
                    document.querySelectorAll('.addEdit-block .textarea .el-textarea__inner').forEach(el=>{
                        el.style.height = this.addEditForm.textareaHeight
                        el.style.color = this.addEditForm.textareaFontColor
                        el.style.fontSize = this.addEditForm.textareaFontSize
                        el.style.borderWidth = this.addEditForm.textareaBorderWidth
                        el.style.borderStyle = this.addEditForm.textareaBorderStyle
                        el.style.borderColor = this.addEditForm.textareaBorderColor
                        el.style.borderRadius = this.addEditForm.textareaBorderRadius
                        el.style.backgroundColor = this.addEditForm.textareaBgColor
                    })
                    document.querySelectorAll('.addEdit-block .textarea .el-form-item__label').forEach(el=>{
                        // el.style.lineHeight = this.addEditForm.textareaHeight
                        el.style.color = this.addEditForm.textareaLableColor
                        el.style.fontSize = this.addEditForm.textareaLableFontSize
                    })
                    // 保存
                    document.querySelectorAll('.addEdit-block .btn .btn-success').forEach(el=>{
                        el.style.width = this.addEditForm.btnSaveWidth
                        el.style.height = this.addEditForm.btnSaveHeight
                        el.style.color = this.addEditForm.btnSaveFontColor
                        el.style.fontSize = this.addEditForm.btnSaveFontSize
                        el.style.borderWidth = this.addEditForm.btnSaveBorderWidth
                        el.style.borderStyle = this.addEditForm.btnSaveBorderStyle
                        el.style.borderColor = this.addEditForm.btnSaveBorderColor
                        el.style.borderRadius = this.addEditForm.btnSaveBorderRadius
                        el.style.backgroundColor = this.addEditForm.btnSaveBgColor
                    })
                    // 返回
                    document.querySelectorAll('.addEdit-block .btn .btn-close').forEach(el=>{
                        el.style.width = this.addEditForm.btnCancelWidth
                        el.style.height = this.addEditForm.btnCancelHeight
                        el.style.color = this.addEditForm.btnCancelFontColor
                        el.style.fontSize = this.addEditForm.btnCancelFontSize
                        el.style.borderWidth = this.addEditForm.btnCancelBorderWidth
                        el.style.borderStyle = this.addEditForm.btnCancelBorderStyle
                        el.style.borderColor = this.addEditForm.btnCancelBorderColor
                        el.style.borderRadius = this.addEditForm.btnCancelBorderRadius
                        el.style.backgroundColor = this.addEditForm.btnCancelBgColor
                    })
                })
            },
            addEditUploadStyleChange() {
                this.$nextTick(()=>{
                    document.querySelectorAll('.addEdit-block .upload .el-upload-list--picture-card .el-upload-list__item').forEach(el=>{
                        el.style.width = this.addEditForm.uploadHeight
                        el.style.height = this.addEditForm.uploadHeight
                        el.style.borderWidth = this.addEditForm.uploadBorderWidth
                        el.style.borderStyle = this.addEditForm.uploadBorderStyle
                        el.style.borderColor = this.addEditForm.uploadBorderColor
                        el.style.borderRadius = this.addEditForm.uploadBorderRadius
                        el.style.backgroundColor = this.addEditForm.uploadBgColor
                    })
                })
            },
        }
    };
</script>
<style lang="scss">
.editor{
    height: 500px;

& /deep/ .ql-container {
      height: 310px;
  }
}
.amap-wrapper {
    width: 100%;
    height: 500px;
}
.search-box {
    position: absolute;
}
.addEdit-block {
    margin: -10px;
}
.detail-form-content {
    padding: 12px;
    background-color: transparent;
}
.btn .el-button {
    padding: 0;
}</style>

