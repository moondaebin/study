<template>
    <div class="infomation"  v-if="modal==false">
  <div class = "cust">
      <ul>
        <li>
          <label for="dop">**작성일자</label>
          <input type="text" id="dop" autofocus
          placeholder="작성 날짜 기입" required>
        </li>
        <li>
          <label for="name">*고객명</label>
          <input type="text" id="name" autofocus
          placeholder="성함" required>
        </li>
        <li>
          <label for="resident">*실명번호</label>
          <input type="password" id="resident" autofocus
          placeholder="주민번호" required>
        </li>
        <li>
          <label for="email">*E-mail</label>
          <input type="email" id="email" autofocus
          placeholder="@ 형태로 입력하세요" required>
        </li>
        <li>
          <label for="number">전화번호</label>
          <input type="text" id="number" autofocus
          placeholder="000-0000-0000" required>
        </li>
        <li>
          <label for="phone">*핸드폰번호</label>
          <input type="text" id="phone" required>
        </li>
        <li>
          <label for="job">*직업</label>
          <input type="text" id="job" required> 
        </li>
        <li>
          <label for="address">주소</label>
          <textarea cols="20" rows="3"></textarea>
        </li>
        </ul>
      </div>
        <hr>
        <div class="manager">
          <ul>
        <li>
          <label for="manager">관리담당자</label>
          <input type="text" id="manager" placeholder="담당자를 선택하세요"
          Disabled="true" required>
          <button class="button_img"></button>
          <!-- 이미지 클릭만 가능하도록 설정 -->
        </li>
        <li>
          <label for="department">**부서</label>
          <input type="text" id="department" Disabled="true" required>
        </li>
        <li>
          <label for="position">**직위</label>
          <input type="text" id="position" Disabled="true" required>
        </li>
        <li>
          <label for="number2">**연락처</label>
          <input type="text" id="number2" Disabled="true" required>
        </li>
      </ul>
      </div>
       <Counsel/>
    </div>
</template>

<script>
import Counsel from '@/assets/counsel';
export default {
    name: "NewCusVue",
    props: {
        modal : Boolean,
    },
    components: {
        Counsel,
    },
}
</script>

<style>
 input[type="password"] , input[type="email"] {
    width: 170px ;
    height: 30px;
 }
</style>
