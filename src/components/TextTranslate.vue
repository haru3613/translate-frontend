<template>
  <div>
    <input type="text" v-model="sourceText" placeholder="輸入要翻譯的文字" />
    <select v-model="targetLanguage">
      <option value="ja">日語</option>
      <option value="zh-tw">繁體中文</option>
      <option value="ko">韓文</option>
      <!-- 你可以添加更多的語言選項 -->
    </select>
    <button @click="fetchTranslation">翻譯</button>
    <p v-if="translatedText">{{ translatedText }}</p>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      sourceText: '',
      targetLanguage: 'ja',
      translatedText: ''
    };
  },
  methods: {
    fetchTranslation() {
      const apiUrl = 'http://localhost:8000/api/translate/';
      const headers = {
        'Content-Type': 'application/json',
      };
      const data = {
        source_text: this.sourceText,
        target_language: this.targetLanguage
      };

      axios.post(apiUrl, data, { headers })
        .then(response => {
          this.translatedText = response.data.translated_text; // 根據 API 的回應格式調整此處
        })
        .catch(error => {
          console.error("API 調用出錯:", error);
        });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
