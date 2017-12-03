FROM ubuntu:18.04

RUN apt update
# tcpで通信するのに必要
RUN apt install -y netbase zlib1g-dev

########################################
## Haskell環境の構築
########################################

# haskellのパッケージマネージャをインストール
RUN apt install -y haskell-stack

# ghcをビルド
RUN stack setup

RUN mkdir -p /root/.stack/global-project/
RUN echo 'extra-deps:\n- roman-numerals-0.5.1.5\n' >> /root/.stack/global-project/stack.yaml

# pandoc他をインストール
# 理論上はビルドに失敗しないはず、祈れ
RUN stack install pandoc pandoc-citeproc pandoc-crossref

########################################
## PATH
########################################

RUN export PATH=$PATH:/root/.local/bin

CMD ["bash"]
