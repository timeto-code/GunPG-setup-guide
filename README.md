# 下载安装 GunPG

根据 [官网](https://gnupg.org/) 提示下载安装指定工具。

## Windows

1. 下载 [Gpg4win](https://www.gpg4win.org/) 并安装。

1. 运行 `gpg --version` 检查安装是否成功。成功安装时会打印如下信息。

    ```bash
    gpg (GnuPG) 2.4.7
    libgcrypt 1.11.0
    Copyright (C) 2024 g10 Code GmbH
    License GNU GPL-3.0-or-later <https://gnu.org/licenses/gpl.html>
    This is free software: you are free to change and redistribute it.
    There is NO WARRANTY, to the extent permitted by law.

    Home: C:\Users\nikiw\AppData\Roaming\gnupg
    Supported algorithms:
    Pubkey: RSA, ELG, DSA, ECDH, ECDSA, EDDSA
    Cipher: IDEA, 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH,
            CAMELLIA128, CAMELLIA192, CAMELLIA256
    Hash: SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
    Compression: Uncompressed, ZIP, ZLIB, BZIP2
    ```

1. 运行 `Kleopatra` 客户端程序。

1. 新建密钥对（证书）。创建结束后可看到 `Key ID` 信息。

1. 配置 `Git` 使用 `GunPG` 进行签名。

    ```bash
    # 明确告诉 Git 使用哪个 GPG 可执行文件来对提交进行签名
    git config --global gpg.program "C:\Program Files (x86)\GnuPG\bin\gpg.exe"
    # 设置签名所用的 GPG 密钥 ID
    git config --global user.signingkey [KeyID]
    # 默认对每次提交进行 GPG 签名
    git config --global commit.gpgsign true
    ```

1. 从 `Kleopatra` 导出公钥。

1. 使用文本编辑器打开导出公钥文件，复制全部内容。如下所示：

    ```
    -----BEGIN PGP PUBLIC KEY BLOCK-----

    mDMEZ5h5xBYJKwYBBAHaRw8BAQdApaRJV3acHb+A0PIec6J7SA1ZtD0db3Dv9XOc
    ****************************************************************
    ****************************************************************
    ****************************************************************
    ****************************************************************
    ****************************************************************
    XjMmHCkkr11IkiKUdQD/SGk7pPony/bvnPTYqAcPwHjDCTQf3CXgt71DNMtocgA=
    =0Jx2
    -----END PGP PUBLIC KEY BLOCK-----
    ```

1. 在 `GitHub` 中点击头像，选择 `Settings` > `SSH and GPG keys` > `New GPG key` 粘贴复制公钥并保持。

## Mac