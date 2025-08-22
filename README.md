# apexGHUB
简单分享一下，见说明，所有数据都是固定的，打开主板模式，就是纯硬件，带着鼠标哪里都能用，数据自己调一下吧，
我用的方式是游戏内录一下屏，然后全屏播放，GHUB里面增加输出，获取坐标，调到自己要用的就行了

-- 甲在盒子内的坐标
points = {
    -- X,Y,Time(ms)
    {7700,43000,5}
}

EnablePrimaryMouseButtonEvents(true)
turn=1
down=1

function OnEvent(event, arg)
    if (event == "MOUSE_BUTTON_PRESSED" and arg == 6) then
        -- 开盒子
        PressKey("e")
        Sleep(500)
        ReleaseKey("e")

        -- 点击事件
        for k, v in ipairs(points) do
            Sleep(5)
            MoveMouseTo(v[1], v[2]);
            Sleep(1)
            PressMouseButton(1)
            Sleep(v[3])
            ReleaseMouseButton(1)
        end

        -- 关闭界面
        Sleep(10)
        PressKey("tab")
        ReleaseKey("tab")
    end
    
    
    
    

    local offset
    local recovery_offset
    local downcount
    local qwq = IsMouseButtonPressed(3)

    if(event== "MOUSE_BUTTON_PRESSED" and arg==1 and turn==1 and qwq==true) then
        downcount=0
        repeat
--          OutputLogMessage("%d\n",downcount)
            downcount=downcount+1
            if(downcount<=150 and down==1) then
                MoveMouseRelative(0,1)
            end

            offset=math.random(9,9)
            recovery_offset = -offset
            Sleep(2)
            MoveMouseRelative(offset,offset)
            Sleep(2)
            MoveMouseRelative(recovery_offset,recovery_offset)
        until not IsMouseButtonPressed(1)
    end



end
