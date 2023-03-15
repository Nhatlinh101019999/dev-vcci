<template>
  <div class="py-5 md:w-1/2 lg:w-2/5">
    <a-steps :current="current">
      <a-step v-for="item in steps" :key="item.title" :title="item.title" />
    </a-steps>
    <div class="">
      <div class="steps-content px-2">
        <template v-if="current===0">
          <div class="text-left px-2">
            <h2 class="text-[#2c2c2c] text-lg font-bold">
              Thông tin doanh nghiệp
            </h2>
            <p class="text-[#2c2c2c] text-sm ">
              Mã số thuế: 0110010000
            </p>
            <p class="text-[#2c2c2c] text-sm ">
              Tên công ty: Moonshine
            </p>
            <p class="text-[#2c2c2c] text-sm ">
              Địa chỉ: 116 Trần Duy Hưng
            </p>
            <p class="text-[#2c2c2c] text-sm ">
              Người đại diện: Trang
            </p>
          </div>
          <a-form-model :model="form" :rules="firstRules">
            <a-form-model-item label="Tên người liên hệ để phối hợp (*)" style="width:100% left:0%" prop="name">
              <a-input v-model="form.name" placeholder="Vui lòng nhập" size="large" />
            </a-form-model-item>
            <a-form-model-item prop="position">
              <a-select
                v-model="form.position"
                placeholder="Vui lòng chọn độ tuổi"
                style="width:100%"
                allow-clear="true"
              >
                <a-select-option value="Chủ tịch/phó chủ tịch">
                  Chủ tịch/phó chủ tịch
                </a-select-option>
                <a-select-option value="giám đốc/phó giám đốc">
                  giám đốc/phó giám đốc
                </a-select-option>
                <a-select-option value="Kế toán trưởng">
                  Kế toán trưởng
                </a-select-option>
                <a-select-option value="Ban lãnh đạo">
                  Ban lãnh đạo
                </a-select-option>
                <a-select-option value="Chủ doanh nghiệps">
                  Chủ doanh nghiệps
                </a-select-option>
              </a-select>
            </a-form-model-item>
            <a-form-model-item label="Email" style="width:100% left:0%" prop="email">
              <a-input placeholder="Vui lòng nhập" size="large" />
            </a-form-model-item>
            <a-form-model-item label="Số điện thoại di động để liên hệ" style="width:100% left:0%" prop="phone">
              <a-input placeholder="Vui lòng nhập" size="large" />
            </a-form-model-item>
            <a-form-model-item prop="age">
              <a-select
                v-model="form.age"
                placeholder="Vui lòng chọn độ tuổi"
                style="width:100%"
                allow-clear="true"
              >
                <a-select-option value="Dưới 26 tuổi">
                  Dưới 26 tuổi
                </a-select-option>
                <a-select-option value="Từ 26 đến 30 tuổi">
                  Từ 26 đến 30 tuổi
                </a-select-option>
                <a-select-option value="Từ 31 đến 40 tuổi">
                  Từ 31 đến 40 tuổi
                </a-select-option>
                <a-select-option value="Từ 41 đến 50 tuổi">
                  Từ 41 đến 50 tuổi
                </a-select-option>
                <a-select-option value="Từ 50 tuổi trở lên">
                  Từ 50 tuổi trở lên
                </a-select-option>
              </a-select>
            </a-form-model-item>
            <a-form-model-item label="Số CMT/CCCD người liên hệ" style="width:100% left:0%" prop="citizen">
              <a-input placeholder="Vui lòng nhập" size="large" />
            </a-form-model-item>
            <a-form-model-item label="Số điện thoại cơ quan nếu có" style="width:100% left:0%">
              <a-input placeholder="Vui lòng nhập" size="large" />
            </a-form-model-item>
          </a-form-model>
        </template>
        <template v-if="current===1">
          <div>
            <div class="content">
              <h2>1.Hiện tại khách hàng của bạn thanh toán bằng hình thức nào?</h2>
            </div>
            <div>
              <a-radio-group>
                <a-radio :style="radioStyle" :value="1">
                  Tiền mặt
                </a-radio>
                <a-radio :style="radioStyle" :value="2">
                  Chuyển khoản
                </a-radio>
                <a-radio :style="radioStyle" :value="3">
                  Quét mã QR
                </a-radio>
                <a-radio :style="radioStyle" :value="4">
                  Quẹt thẻ
                </a-radio>
              </a-radio-group>
            </div>
          </div>
        </template>
        <template v-if="current===1">
          <div>
            <div class="content">
              <h2>2.Cách thức bạn đối soát doanh thu hiện tại?</h2>
            </div>
            <div>
              <a-radio-group>
                <a-radio :style="radioStyle" :value="10">
                  Đối soát thủ công bằng cách kiểm tra các giao dịch
                </a-radio>
                <a-radio :style="radioStyle" :value="20">
                  Đối soát tự động
                </a-radio>
              </a-radio-group>
            </div>
          </div>
        </template>
        <template v-if="current===1">
          <div>
            <div class="content">
              <h2>3.Với hình thức thanh toán hiện tại cần xác minh giao dịch như thế nào?</h2>
            </div>
            <div>
              <a-radio-group>
                <a-radio :style="radioStyle" :value="1">
                  Chụp ảnh màn hình thanh toán của khách
                </a-radio>
                <a-radio :style="radioStyle" :value="2">
                  Xác minh tự động trên app thanh toán
                </a-radio>
                <a-radio :style="radioStyle" :value="3">
                  Xác minh qua thông báo số dư ngay lập tức tới tài khoản ngân hàng
                </a-radio>
                <a-radio :style="radioStyle" :value="4">
                  Chưa có hình thức xác minh nào
                </a-radio>
              </a-radio-group>
            </div>
          </div>
        </template>
        <template v-if="current===1">
          <div>
            <div class="content">
              <h2>4.Bạn đã từng bị thất thoát doanh thu do quá trình thanh toán của khách hàng hoặc do nhầm nhẫn từ nhân viên không?</h2>
            </div>
            <div>
              <a-radio-group>
                <a-radio :style="radioStyle" :value="1">
                  Rất nhiều lần
                </a-radio>
                <a-radio :style="radioStyle" :value="2">
                  Chưa từng
                </a-radio>
                <a-radio :style="radioStyle" :value="3">
                  Đã từng
                </a-radio>
                <a-radio :style="radioStyle" :value="4">
                  Khoản thất thoát trong giới hạn chấp nhận
                </a-radio>
              </a-radio-group>
            </div>
          </div>
        </template>
        <template v-if="current===1">
          <div>
            <div class="content">
              <h2>5.Nếu chưa sử dụng, bạn có sẵn lòng áp dụng phương thức thanh toán bằng QR Code không?</h2>
            </div>
            <div>
              <a-radio-group>
                <a-radio :style="radioStyle" :value="1">
                  Có
                </a-radio>
                <a-radio :style="radioStyle" :value="2">
                  Không
                </a-radio>
              </a-radio-group>
            </div>
          </div>
        </template>
        <template v-if="current===2">
          <div>
            <div class="content">
              <h2>6.Bạn có muốn sử dụng hình thức thanh toán do ngân hàng trực tiếp cung cấp đi kèm nhiều ưu đãi từ ngân hàng không?</h2>
            </div>
            <div>
              <a-radio-group v-model="value" @change="onChange">
                <a-radio :style="radioStyle" :value="1">
                  Có
                </a-radio>
                <a-radio :style="radioStyle" :value="2">
                  Không
                </a-radio>
              </a-radio-group>
            </div>
            <div class="content">
              <h2>7.Bạn mong muốn có thể hoàn tất toàn bộ quy trình qua đăng ký online không?</h2>
            </div>
            <div>
              <a-radio-group>
                <a-radio :style="radioStyle" :value="1">
                  Hoàn tất Online
                </a-radio>
                <a-radio :style="radioStyle" :value="2">
                  Hoàn tất với hỗ trợ
                </a-radio>
              </a-radio-group>
            </div>
            <div class="content">
              <h2>8.Với hình thức thanh toán mới, bạn có mong muốn áp dụng phương thức đối soát và xác minh giao dịch tự động không?</h2>
            </div>
            <div>
              <a-radio-group>
                <a-radio :style="radioStyle" :value="1">
                  Rất mong muốn
                </a-radio>
                <a-radio :style="radioStyle" :value="2">
                  Có cũng được
                </a-radio>
                <a-radio :style="radioStyle" :value="3">
                  Không có nhu cầu
                </a-radio>
              </a-radio-group>
            </div>
            <div class="content">
              <h2>9.Bạn có muốn sử dụng miễn phí phần mềm Myshop và máy thanh toán Paybox không?</h2>
            </div>
            <div>
              <a-radio-group>
                <a-radio :style="radioStyle" :value="1">
                  Có
                </a-radio>
                <a-radio :style="radioStyle" :value="2">
                  Không
                </a-radio>
                <a-radio :style="radioStyle" :value="3">
                  Xem xét sử dụng
                </a-radio>
              </a-radio-group>
            </div>
            <div class="content">
              <h2>10.Nếu có, bạn mong muốn hoàn thành lắp đặt sau bao nhiêu ngày?</h2>
            </div>
            <div>
              <a-radio-group>
                <a-radio :style="radioStyle" :value="1">
                  1 ngày
                </a-radio>
                <a-radio :style="radioStyle" :value="2">
                  2 ngày
                </a-radio>
                <a-radio :style="radioStyle" :value="3">
                  3 ngày
                </a-radio>
              </a-radio-group>
            </div>
          </div>
        </template>
      </div>
    </div>
    <div class="steps-action">
      <a-button v-if="current < steps.length - 1" type="navigation" @click="next">
        Next
      </a-button>
      <a-button
        v-if="current == steps.length - 1"
        type="navigation"
        @click="$message.success('Bạn đã hoàn thành liên hệ')"
      >
        Done
      </a-button>
      <a-button v-if="current > 0" style="margin-left: 8px" @click="prev">
        Back
      </a-button>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      current: 0,
      form: {
        name: '',
        age: '',
        position: ''
      },
      radioStyle: {
        display: 'block',
        height: '30px',
        lineHeight: '30px'
      },
      value: '',
      steps: [
        {
          title: 'Bước 1',
          content: 'First-content'
        },
        {
          title: 'Bước 2',
          content: 'Second-content'
        },
        {
          title: 'Bước 3',
          content: 'Last-content'
        }
      ],
      firstRules: {
        name: [
          { required: true, message: 'Vui lòng nhập tên', trigger: 'change' }
        ],
        age: [
          { required: true, message: 'Vui lòng chọn độ tuổi ', trigger: 'change' }
        ],
        email: [
          { required: true, message: 'Vui lòng nhập email ', trigger: 'change' }
        ],
        phone: [
          { required: true, message: 'Vui lòng nhập số điện thoại ', trigger: 'change' }
        ],
        citizen: [
          { required: true, message: 'Vui lòng nhập số CCCD ', trigger: 'change' }
        ],
        position: [
          { required: true, message: 'Vui lòng chọn chức vụ ', trigger: 'change' }
        ]
      }
    }
  },
  methods: {
    next () {
      this.current++
    },
    prev () {
      this.current--
    },
    onChange (e) {
      console.log('radio checked', e.target.value)
      if (e.target.value === 1) {
        console.log('vào')
        window.open('https://www.youtube.com/watch?v=MZUAusD-Zy0&list=RDMZUAusD-Zy0&start_radio=1', '_blank')
      }
    }
  }
}
</script>
<style scoped>
.steps-content {
  margin-top: 16px;
  border: 1px dashed #e9e9e9;
  border-radius: 6px;
  background-color: #fafafa;
  min-height: 200px;
  padding-top: 20px;
  border-radius: 0.5rem;
    box-shadow: 0 4px 25px 0 rgba(0,0,0,.1);
}

.steps-action {
  margin-top: 24px;
}
</style>
