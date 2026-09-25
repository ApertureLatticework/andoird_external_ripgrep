# android_external_ripgrep

Operit `liboperit_ripgrep`（rg 内容搜索 JNI 桥）的树内源码线依赖仓。

## 职责

vendor ripgrep 家族及其断代依赖，配 Soong `rust_library` 模块；
借树不重复造（jni 0.21.1 / serde 系 1.x / memchr / bstr / walkdir 等直接
引 `external/rust/android-crates-io` 既有模块）。

## 模块清单

| 目录 | 模块 | 树内避让原因 |
| --- | --- | --- |
| aho-corasick-1.1.4 | liboperit_aho_corasick | 树内 0.7 断代 |
| regex-syntax-0.8.11 | liboperit_regex_syntax | 树内 0.6 断代 |
| regex-automata-0.4.14 | liboperit_regex_automata | 树内 0.1 断代 |
| globset-0.4.18 | liboperit_globset | 树内无 |
| grep-matcher-0.1.8 | liboperit_grep_matcher | 树内无 |
| grep-regex-0.1.14 | liboperit_grep_regex | 树内无 |
| ignore-0.4.27 | liboperit_ignore | 树内无 |

## 版本纪律

版本唯一真源为 Operit 仓 `tools/native_ripgrep/Cargo.lock`；
升级时两侧同步，禁单边漂移。features 显式列出，不赌 cargo default。

## 挂载

local_manifests 挂 `path="external/operit-ripgrep"`（AOSP 树内并无
ripgrep 仓，此名纯为自明归属）。
