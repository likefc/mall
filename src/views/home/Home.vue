<template>
  <div id='home'>
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banners='banners'></home-swiper>
    <home-recommend :recommends='recommends'></home-recommend>
    <home-feature></home-feature>
    <tab-control class='tab-control' :titles="['流行', '新款', '潮流']"></tab-control>
    <ul>
      <li>1111</li>
      <li>1112</li>
      <li>1113</li>
      <li>1114</li>
      <li>1115</li>
      <li>1116</li>
      <li>1117</li>
      <li>1118</li>
      <li>1119</li>
      <li>11110</li>
      <li>11111</li>
      <li>11112</li>
      <li>11113</li>
      <li>11114</li>
      <li>11115</li>
      <li>11116</li>
      <li>11117</li>
      <li>11118</li>
      <li>11119</li>
      <li>11120</li>
      <li>11121</li>
      <li>11122</li>
      <li>11123</li>
      <li>11124</li>
      <li>11125</li>
      <li>11126</li>
      <li>11127</li>
      <li>11128</li>
      <li>11129</li>
      <li>11130</li>
      <li>11131</li>
      <li>11132</li>
      <li>11133</li>
      <li>11134</li>
      <li>11135</li>
      <li>11136</li>
      <li>11137</li>
      <li>11138</li>
      <li>11139</li>
      <li>11140</li>
      <li>11141</li>
      <li>11142</li>
      <li>11143</li>
      <li>11144</li>
      <li>11145</li>
      <li>11146</li>
      <li>11147</li>
      <li>11148</li>
      <li>11149</li>
      <li>11150</li>
      <li>11151</li>
      <li>11152</li>
      <li>11153</li>
      <li>11154</li>
      <li>11155</li>
      <li>11156</li>
      <li>11157</li>
      <li>11158</li>
      <li>11159</li>
      <li>11160</li>
      <li>11161</li>
      <li>11162</li>
      <li>11163</li>
      <li>11164</li>
      <li>11165</li>
      <li>11166</li>
      <li>11167</li>
      <li>11168</li>
      <li>11169</li>
      <li>11170</li>
      <li>11171</li>
      <li>11172</li>
      <li>11173</li>
      <li>11174</li>
      <li>11175</li>
      <li>11176</li>
      <li>11177</li>
      <li>11178</li>
      <li>11179</li>
      <li>11180</li>
      <li>11181</li>
      <li>11182</li>
      <li>11183</li>
      <li>11184</li>
      <li>11185</li>
      <li>11186</li>
      <li>11187</li>
      <li>11188</li>
      <li>11189</li>
      <li>11190</li>
      <li>11191</li>
      <li>11192</li>
      <li>11193</li>
      <li>11194</li>
      <li>11195</li>
      <li>11196</li>
      <li>11197</li>
      <li>11198</li>
      <li>11199</li>
      <li>111100</li>
    </ul>
  </div>
</template>
<script>
import NavBar from 'components/common/navbar/NavBar'
import TabControl from 'components/content/tabControl/TabControl'

import HomeSwiper from './childComponent/HomeSwiper'
import HomeRecommend from './childComponent/HomeRecommend'
import HomeFeature from './childComponent/HomeFeature'

import { getHomeMultidata } from 'network/home'
export default {
  name: 'Home',
  data() {
    return {
      banners: [],
      recommends: []
    }
  },
  created() {
    //  请求多个数据
    getHomeMultidata().then(res => {
      const { banner, recommend } = res.data
      this.banners = banner.list
      this.recommends = recommend.list
    })
  },
  components: {
    NavBar,
    HomeSwiper,
    HomeRecommend,
    HomeFeature,
    TabControl
  }
}
</script>
<style>
#home {
  padding-top: 44px;
  padding-bottom: 50px;
}
.home-nav {
  text-align: center;
  background-color: var(--color-tint);
  color: #fff;

  position: fixed;
  top: 0;
  right: 0;
  left: 0;
  z-index: 100;
}
.tab-control {
  position: sticky;
  top: 44px;
  background-color: #fff;
}
</style>
