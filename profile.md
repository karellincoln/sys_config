## system startup system

### checking whether computer has a extern keyboard.

```
# 如果有外接USB键盘鼠标则禁用笔记本键盘触摸板

SLEEP_TIME=5

# 自带的键盘触摸板名字
KEYBOARD_DEV='AT Translated Set 2 keyboard'

# 外接的键盘触摸板名字
USB_KEYBOARD_DEV='Topre Corporation HHKB Professional'

while true
do
    # 处理键盘的逻辑
    HAVE_USB_KEYBOARD=`xinput list | grep "$USB_KEYBOARD_DEV"`
    if [ "" != "$HAVE_USB_KEYBOARD" ]; then
        xinput set-prop "$KEYBOARD_DEV" 'Device Enabled' 0
        # echo Disable keyboard
    else
        xinput set-prop "$KEYBOARD_DEV" 'Device Enabled' 1
        # echo Enable keyboard
    fi
    sleep $SLEEP_TIME
done

```

add above code in ~/.profile.

