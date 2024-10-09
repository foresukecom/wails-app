# ベースイメージとして公式のGoイメージを使用
FROM golang:1.23-bullseye

# 必要なパッケージをインストール
RUN apt-get update && apt-get install -y \
    libgtk-3-dev \
    libwebkit2gtk-4.0-dev \
    xorg \
    dbus-x11

# ユーザーを作成
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME

# Wails CLIのインストール
RUN go install github.com/wailsapp/wails/v2/cmd/wails@latest

# パスの設定
ENV PATH="/go/bin:${PATH}"

# 作業ディレクトリの設定
WORKDIR /workspace