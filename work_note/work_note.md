
# mail包升级到1.47后，内部邮箱发送时认证失败
props.put("mail.smtp.auth", "true");后面加上(两个地方)props.setProperty("mail.smtp.ehlo", "false");

