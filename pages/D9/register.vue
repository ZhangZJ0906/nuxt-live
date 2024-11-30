<script setup>
const { $swal } = useNuxtApp();
const api_url = "https://nuxr3.zeabur.app/"

// 表單格式
const userRegisteObject = ref({
    name: "",
    email: "",
    password: "",
    phone: "",
    birthday: "",
    address: {
        zipcode: "",
        detail: "",
    },
});
const isSubmitting = ref(false);

const userRegiste = async () => {
    if (isSubmitting.value) return; // 防止重複提交
    
    isSubmitting.value = true;
    try {
        const response = await fetch(api_url + "api/v1/user/signup", {
            body: JSON.stringify(userRegisteObject.value),
            method: "POST",
            headers: {
                "Content-Type": "application/json",
            },
        });
        
        const data = await response.json(); // 假設 API 回傳 JSON 資料
        
        if (!response.ok) throw new Error(data.message || '註冊失敗');
        
        $swal.fire({
            icon: "success",
            title: "註冊成功",
            text: data.message || "已成功註冊",
            confirmButtonText: "OK",
        });
    } catch (error) {
        console.error("API 调用失败：", error);
        $swal.fire({
            icon: "error",
            title: "註冊失敗",
            text: error.message,
            confirmButtonText: "OK",
        });
    } finally {
        isSubmitting.value = false;
    }
};
// 使用 sweetAlert2 套件顯示訊息
// $swal.fire({
//   position: "center",
//   icon: ...,
//   title: ...,
//   showConfirmButton: false,
//   timer: 1500,
// });
</script>

<template>
    <div class="bg-light py-3 py-md-5 vh-100">
        <div class="container">
            <div class="row justify-content-md-center">
                <div class="col-12 col-md-11 col-lg-8 col-xl-7 col-xxl-6">
                    <div class="bg-white p-4 p-md-5 rounded shadow-sm">
                        <h2 class="h3 mb-4">會員註冊</h2>
                        <form @submit.prevent="userRegiste">
                            <div class="form-floating mb-4">
                                <input type="text" class="form-control" id="firstName" placeholder="王小明" required v-model="userRegisteObject.name" />
                                <label for="firstName">姓名 <span class="text-danger">*</span></label>
                            </div>

                            <div class="form-floating mb-4">
                                <input type="email" class="form-control" id="email" placeholder="example@gmail.com"
                                    pattern="[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}$" required  v-model="userRegisteObject.email"/>
                                <label for="email">信箱 <span class="text-danger">*</span></label>
                            </div>

                            <div class="form-floating mb-4">
                                <input type="password" class="form-control" id="password" placeholder="請輸入 8 碼以上密碼" v-model="userRegisteObject.password"
                                    pattern=".{8,}" required />
                                <label for="password">密碼 <span class="text-danger">*</span></label>
                            </div>

                            <div class="form-floating mb-4">
                                <input type="tel" class="form-control" id="phone" placeholder="0912345678" v-model="userRegisteObject.phone"
                                    pattern="(\+886|0)?9\d{8}|(\+886|0)?2\d{8}|\d{3}-\d{4}-\d{4}" required />
                                <label for="phone">電話</label>
                            </div>

                            <div class="form-floating mb-4">
                                <input type="date" class="form-control" id="dateInput" required v-model="userRegisteObject.birthday"/>
                                <label for="dateInput">出生年月日</label>
                            </div>

                            <div class="row">
                                <div class="col-md-6">
                                    <div class="form-floating mb-4">
                                        <input type="text" class="form-control" id="zipcode" placeholder="100" v-model="userRegisteObject.address.zipcode"
                                            pattern="\d{3,}" required />
                                        <label for="zipcode">郵遞區號</label>
                                    </div>
                                </div>
                                <div class="col-md-6">
                                    <div class="form-floating mb-4">
                                        <input type="text" class="form-control" id="address" placeholder="台北市中正區重慶南路一段" v-model="userRegisteObject.address.detail"
                                            required />
                                        <label for="address">詳細地址</label>
                                    </div>
                                </div>
                            </div>

                            <button class="btn btn-lg btn-primary w-100" type="submit" :disabled="isSubmitting" >
                                註冊
                            </button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped></style>