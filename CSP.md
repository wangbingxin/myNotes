## CSP(Content Security Polity,内容安全策略)

主要是用来定义页面可以加载哪些资源，减少 XSS 的发生。

#### 两种方式启用CSP的指令：

> HTTP响应头方式：
  ` Content-Security-Policy: default-src 'self'`

> `<meta>`标签方式:
  `<meta http-equiv="Content-Security-Policy" content="default-src 'self'">`
  default-src 是 CSP 指令，多个指令之间用英文分号分割；'self' 是指令值，多个指令值用英文空格分割。

非 HTTPS 资源都不允许加载：
	HTTP 响应头方式：
`Content-Security-Policy: block-all-mixed-content`
　　`<meta>` 标签方式：
`<meta http-equiv="Content-Security-Policy" content="block-all-mixed-content">`

参考链接：<https://developer.mozilla.org/zh-CN/docs/Web/Security/CSP/CSP_policy_directives>
          <https://developer.mozilla.org/zh-CN/docs/Web/Security/CSP/CSP_policy_directives>
          <https://imququ.com/post/content-security-policy-reference.html>
