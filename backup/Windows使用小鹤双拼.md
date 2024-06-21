## 开启小鹤双拼 ##
```
Windows Registry Editor Version 5.00
[HKEY_CURRENT_USER\SOFTWARE\Microsoft\InputMethod\Settings\CHS]
"EnableExtraDomainType"=dword:00000001
"EnableSmartSelfLearning"=dword:00000000
"EnableVMode"=dword:00000000
"EnableHap"=dword:00000000
"EnablePeopleName"=dword:00000000
"DoublePinyinScheme"=dword:0000000a
"EnableUMode"=dword:00000000
"EnableSmartFuzzyPinyin"=dword:00000000
"UserDefinedDoublePinyinScheme0"="小鹤双拼*2*^*iuvdjhcwfg^xmlnpbksqszxkrltvyovt"
"Enable Dynamic Candidate Ranking"=dword:00000000
"Enable self-learning"=dword:00000000
"Expand Double Pinyin"=dword:00000000
"Enable Double Pinyin"=dword:00000001
"LangBar Force On"=dword:00000000
"PinyinMixEnable"=dword:00000000
"ToolBarEnabled"=dword:00000000
```
## 关闭小鹤双拼 ##
```
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\SOFTWARE\Microsoft\InputMethod\Settings\CHS]
"Enable Double Pinyin"=dword:00000000
"DoublePinyinScheme"=dword:00000000
"UserDefinedDoublePinyinScheme0"=-
```

以上两个代码块保存为reg添加到注册表即可