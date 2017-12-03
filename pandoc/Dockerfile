FROM ubuntu:18.04

RUN apt update
# tcpで通信するのに必要
RUN apt install -y netbase zlib1g-dev

########################################
## Haskell環境の構築
########################################

# haskellのパッケージマネージャをインストール
RUN apt install -y haskell-stack

# ltsを固定
RUN mkdir -p /root/.stack/global-project/
ADD stack.yaml /root/.stack/global-project

# ghcをビルド
RUN stack setup


# pandoc他をインストール
# 理論上はビルドに失敗しないはず、祈れ
RUN stack install pandoc pandoc-citeproc pandoc-crossref

CMD ["bash"]
