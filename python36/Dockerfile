FROM python:3.6

RUN pip config set global.index-url https://bkrepo.cwoa.net/pypi/aiops/kingeye-pypi/simple

# 使用清华大学镜像源
RUN sed -i 's/deb.debian.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list
RUN sed -i 's/security.debian.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list

# 安装SSH服务器
RUN apt-get update && apt-get install -y openssh-server
RUN mkdir /var/run/sshd

# 设置root用户密码（注意：这只是个例子，请使用更安全的方法）
RUN echo 'root:123456' | chpasswd

# 允许root用户通过SSH登录
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# Expose SSH port
EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
