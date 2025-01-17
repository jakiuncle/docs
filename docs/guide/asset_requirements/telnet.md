# Telnet 资产要求

!!! tip "提示"
    - JumpServer 通过 Telnet 协议和资产建立连接时，无法确认服务端返回的字符是否表示连接成功，所以需要配正则表达式来确认是否连接成功。
    - 需要在 Web `系统设置`-`终端设置` 中添加成功判断代码。

!!! tip "通过 `telnet` 命令登录 telnet设备 `成功` 的返回字符串"
    - 举例：

    ```sh
    telnet 172.16.0.1
    ```
    ```vim
    Login authentication  
    login: admin  
    password: *********  
    Info: The max number or VTY users is 10, and the number  
          of current VTY users on line is 1.  
    <RA-L7-RD>
    <RA-L7-RD> system-view

    ```

    - 把 `<RA-L7-RD>` 写入到 Web "系统设置"-"终端设置"-"Telnet 成功正则表达式" 里面
    - `<RA-L7-RD> 正则可用 <.*> 表示 或者 <RA-.*>`
    - `RW-F1-1  正则可用 RW-.*`

!!! tip "不会写正则直接写设备名就行，`设备1名|设备2名|设备3名|设备4名|success|成功`"
    - `RW-1F-1|RW-2F-1|RW-3F-1|success|成功`
    - `<RA-L7-RD>|<RA-L6-RD>|<RA-L5-RD>|success|成功`
    - `<.*>|.*>|success|成功`
