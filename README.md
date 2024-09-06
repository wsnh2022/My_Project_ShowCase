# My_Project_PNG 

[The-Ultimate-Markdown-Cheat-Sheet](https://github.com/lifeparticle/Markdown-Cheatsheet)

## 💡ONE GUI Tab-1: Main
![Description of the image](My_AHK_Project_Snaps/ONE_GUI.png "ONE_GUI.png")

## ONE GUI Tab-2 : Templates Manager
![Description of the image](My_AHK_Project_Snaps/ONE_GUI_Templates_Manager.png "ONE_GUI_Templates_Manager")


## AHK ONE GUI SOURCE CODE

<details>
<summary>Click to expand/collapse the code</summary>

```autohotkey
#Requires AutoHotkey v2.0+
#SingleInstance Force
TraySetIcon "hexlock.ico"
#Include C:\Users\The_Thinker\Documents\AutoHotkey_V2\V2Functions.ahk
#Include C:\Users\The_Thinker\Documents\AutoHotkey_V2\lib\GuiEnhancerKit.ahk
#Include C:\Users\The_Thinker\Documents\AutoHotkey_V2\lib\ColorButton.ahk

; Hotkeys
~!Space::Reload()

MyheaderFontsize := "s12", MyFontsize := "s10", MyFont := "Calibri" ; "Bahnschrift" ; "Cascadia Code" "Consolas", "Arial"
; THEME COLOR
bc := "0a0a0a", Hfc := "ff0909", Fc := "9375ff"  ; Blue-Red Theme

; GUI creation
MyGui := GuiExt()
; MyGui.Opt("+AlwaysOnTop")
MyGui.Title := "OneGui"
MyGui.BackColor := bc
MyGui.SetWindowAttribute(33, 2) ;;To set Rounded Corners for window.
MyGui.SetDarkTitle()
MyGui.SetDarkMenu()
MyGui.SetWindowColor(, MyGui.BackColor, MyGui.BackColor)
MyGui.SetFont("s9 ca888ff", MyheaderFontsize)

; Create TabView
TabView := MyGui.Add("Tab3", "x2 y2 w595 h395")
TabView.Add(["Main", "Template Manager"])

; Main Tab
TabView.UseTab(1)
{

MyGui.SetFont("s12 cff0000")
MyGui.Add("Text", "x7 y25 c" . Hfc, "Search")

MyGui.SetFont(MyFontsize, MyFont)
MyGui.Add("CheckBox", "x9 y+2 c" . Fc, "DuckDuckGo").Name := "C1"
MyGui.Add("CheckBox", "x9 y+2 c" . Fc, "Google").Name := "C2"
MyGui.Add("CheckBox", "x9 y+2 c" . Fc, "YouTube").Name := "C3"
MyGui.Add("CheckBox", "x9 y+2 c" . Fc, "Quora").Name := "C23"
MyGui.Add("CheckBox", "x9 y+2 c" . Fc, "Reddit").Name := "C4"
MyGui.Add("CheckBox", "x9 y+2 c" . Fc, "Amazon").Name := "C5"
MyGui.Add("CheckBox", "x9 y+2 c" . Fc, "FlipKart").Name := "C6"
MyGui.Add("CheckBox", "x9 y+2 c" . Fc, "WolframAlpha").Name := "C7"

MyGui.SetFont(MyheaderFontsize)
MyGui.Add("Text", "x140 y25 c" . Hfc, "Ask-Reddit")

MyGui.SetFont(MyFontsize, MyFont)
MyGui.Add("CheckBox", "x140 y44 c" . Fc, "r/learnprogramming (3.5m)").Name := "C8"
MyGui.Add("CheckBox", "x140 y+2 c" . Fc, "r/AutoHotkey (21.0k)").Name := "C9"
MyGui.Add("CheckBox", "x140 y+2 c" . Fc, "r/Excel (595k)").Name := "C10"
MyGui.Add("CheckBox", "x140 y+2 c" . Fc, "r/vbscript (948)").Name := "C11"
MyGui.Add("CheckBox", "x140 y+2 c" . Fc, "r/learnpython (652k)").Name := "C12"
MyGui.Add("CheckBox", "x140 y+2 c" . Fc, "r/Batch (4.0k)").Name := "C13"
MyGui.Add("CheckBox", "x140 y+2 c" . Fc, "r/PowerShell (207k)").Name := "C14"
MyGui.Add("CheckBox", "x140 y+2 c" . Fc, "r/AutomateYourself(2.9k)").Name := "C15"

MyGui.SetFont(MyheaderFontsize)
MyGui.Add("Text", "x7 y220 c" . Hfc, "Social Media")

MyGui.SetFont(MyFontsize, MyFont)
MyGui.Add("CheckBox", "x9 y240 c" . Fc, "Instagram").Name := "C16"
MyGui.Add("CheckBox", "x9 y+2 c" . Fc, "Twitter").Name := "C17"
MyGui.Add("CheckBox", "x9 y+2 c" . Fc, "LinkedIn").Name := "C18"

MyGui.SetFont(MyheaderFontsize)
MyGui.Add("Text", "x140 y220 c" . Hfc, "Search AI")

MyGui.SetFont(MyFontsize, MyFont)
MyGui.Add("CheckBox", "x140 y+2 c" . Fc, "ChatGPT").Name := "C19"
MyGui.Add("CheckBox", "x140 y+2 c" . Fc, "BardAI").Name := "C20"
MyGui.Add("CheckBox", "x140 y+2 c" . Fc, "AHK V1 Doc").Name := "C21"
MyGui.Add("CheckBox", "x140 y+2 c" . Fc, "AHK V2 Doc").Name := "C22"

; Input Search Box And Buttons
MyGui.SetFont(MyFontsize, MyFont)
Ed := MyGui.Add("Edit", "x10 y340 w300 h22 Background000000")

;; Button color - button font color - button border color
btclor := "7c1010", bfont := "cffffff", bBorder := "ffffff"

; Input field Below Buttons

btn := MyGui.Add("Button", "x10 y370 w50 h20 Default", "Search"),btn.OnEvent("Click", Search),btn.SetColor(btclor, bfont, , bBorder,9),btn.SetFont("s10 bold")
btn := MyGui.Add("Button", "x+10 y370 w50 h20", "Clear"),btn.OnEvent("Click", (*) => Ed.Text := ""),btn.SetColor(btclor, bfont, , bBorder, 9),btn.SetFont("s10 bold")
btn := MyGui.Add("Button", "x+10 y370 w60 h20", "Open.XL"),btn.OnEvent("Click", (*) => Run("C:\Users\" A_UserName "\OneDrive\Documents\MyAHK_CheckBox_LIst.xlsx")),btn.SetColor(btclor, bfont, , bBorder, 9),btn.SetFont("s10 bold")
btn := MyGui.Add("Button", "x+10 y370 w30 h20", "Edit"),btn.OnEvent("Click", (*) => Run("C:\Users\" A_UserName "\AppData\Local\Programs\Microsoft VS Code\Code.exe " A_ScriptFullPath)),btn.SetColor(btclor, bfont, , bBorder, 9),btn.SetFont("s10 bold")
btn := MyGui.Add("Button", "x+10 y370 w70 h20", "hibernate"),btn.OnEvent("Click", (*) => Run("C:\Users\The_Thinker\Documents\AutoHotkey\Daily_Ahk\hibernate.bat")),btn.SetColor(btclor, bfont, , bBorder, 9),btn.SetFont("s10 bold")

; Right Corner Column 1 Buttons
MyGui.SetFont("s11")
MyGui.Add("Text", "x340 y25 c" . Hfc, "System")

MyGui.SetFont(MyFontsize, MyFont)
MyGui.Add("Button", "x340 y45 w50 h15", "startup").OnEvent("Click", (*) => Run(A_Startup))
MyGui.Add("Button", "x340 y+10 w50 h15", "chrmap").OnEvent("Click", (*) => Run("charmap.exe"))
MyGui.Add("Button", "x340 y+10 w50 h15", "tskmgr").OnEvent("Click", (*) => Run("Taskmgr.exe"))
MyGui.Add("Button", "x340 y+10 w50 h15", "ahkspy").OnEvent("Click", (*) => Run("C:\ProgramData\Microsoft\Windows\Start Menu\Programs\AutoHotkey Window Spy.lnk"))
MyGui.Add("Button", "x340 y+10 w50 h15", "dxdiag").OnEvent("Click", (*) => Run("dxdiag.exe"))

; Right Corner Column 2 Buttons
MyGui.SetFont("s11")
MyGui.Add("Text", "x400 y25 c" . Hfc, "Scripts")

MyGui.SetFont(MyFontsize, MyFont)
MyGui.Add("Button", "x400 y45 w50 h15", "RPA").OnEvent("Click", (*) => Run(A_MyDocuments "\AutoHotkey_V2\lib\RPA\Macro Recorder.ahk"))
MyGui.Add("Button", "x400 y+10 w50 h15", "date+").OnEvent("Click", Adddate)
MyGui.Add("Button", "x400 y+10 w50 h15", "PassG").OnEvent("Click", (*) => Run(A_MyDocuments "\AutoHotkey\Daily_Ahk\My_Fav\Pwd_Generator.ahk"))
MyGui.Add("Button", "x400 y+10 w50 h15", "%Find").OnEvent("Click", (*) => Run(A_MyDocuments "\AutoHotkey\Daily_Ahk\My_Fav\Percentage_calculater_v2.ahk"))
MyGui.Add("Button", "x400 y+10 w50 h15", "Open").OnEvent("Click",(*) => Run("C:\Users\" A_UserName "\AppData\Local\Programs\Microsoft VS Code\Code.exe " A_MyDocuments "\AutoHotkey_V2\OneMenu.ahk"))
MyGui.Add("Button", "x400 y+10 w50 h15", "Close").OnEvent("Click", close_working)

MyGui.SetFont("s10 c9375ff")
MyGui.Add("Text", "x520 y45 w70 h15", "M-Record").OnEvent("Click", (*) => Run(A_MyDocuments "\AutoHotkey_V2\AutoHotkey_version_2\projects\RecordMouseClicks\RecordMouseClicks_GUI.ahk"))
MyGui.Add("Text", "x520 y+5 w70 h50", "Windows Icon").OnEvent("Click", (*) => Run(A_MyDocuments "\AutoHotkey_V2\AutoHotkey_version_2\projects\icon-enumeration-script.ahk"))
MyGui.Add("Text", "x520 y+5 w70 h50", "All Snippets").OnEvent("Click", (*) => Run("C:\Users\The_Thinker\Documents\AutoHotkey_V2\AutoHotkey_version_2\projects\GUI\Hotstring Gui\My Snippets GUI.ahk"))

; Right Corner Column 3 Buttons for websites
MyGui.SetFont("s11")
MyGui.Add("Text", "x460 y25 c" . Hfc, "Website")

MyGui.SetFont(MyFontsize, MyFont)
MyGui.Add("Button", "x460 y45 w50 h15", "Gkeep").OnEvent("Click", (*) => Run("https://keep.google.com/#home"))
MyGui.Add("Button", "x460 y+10 w50 h15", "v1Doc").OnEvent("Click", v1Doc)
MyGui.Add("Button", "x460 y+10 w50 h15", "v2Doc").OnEvent("Click", v2Doc)
MyGui.Add("Button", "x460 y+10 w50 h15", "T-mail").OnEvent("Click", (*) => Run("https://temp-mail.org/en/"))
MyGui.Add("Button", "x460 y+10 w50 h15", "Achart").OnEvent("Click", (*) => Run("https://www.livechart.me/schedule"))
MyGui.Add("Button", "x460 y+10 w50 h15", "stock").OnEvent("Click", stock_check)
MyGui.Add("Button", "x460 y+10 w50 h15", "Windy").OnEvent("Click", (*) => Run("https://www.windy.com/-Rain-thunder-rain?rain,13.208,80.002,7"))
MyGui.Add("Button", "x460 y+10 w50 h15", "notion").OnEvent("Click", (*) => Run("https://www.notion.so/"))

; Click image to Action
MyGui.Add("Picture", "x360 y285 w25 h25", "C:\Users\" A_UserName "\Pictures\ICO\reddit.ico").OnEvent("Click", (*) => Run("https://www.reddit.com/"))
MyGui.Add("Picture", "x+10 w25 h25", "C:\Users\" A_UserName "\Pictures\medium.png").OnEvent("Click", (*) => Run("https://medium.com/"))
MyGui.Add("Picture", "x+10 w25 h25", "C:\Users\" A_UserName "\Pictures\Crunchyroll.png").OnEvent("Click", (*) => Run("https://www.crunchyroll.com/videos/new?lang=sub"))
MyGui.Add("Picture", "x+10 w25 h25", "C:\Users\" A_UserName "\Pictures\refresh.png").OnEvent("Click", Ra)
}

TabView.UseTab(2)
{
templateDir := A_ScriptDir "\Templates"

; Create the main GUI window
; /** @var {GuiExt} MyGui */
MyGui.BackColor := "0a0a0a"
MyGui.SetFont("s10 c03000c") ;"Cascadia Code" "Trebuchet MS"

; Create a ListView to display template files
LV := MyGui.Add("ListView", "r7 x7 y25 w210 h340 Background0a0a0a cFFFFFF", ["Template Name               Sort ↕️"])
LV.OnEvent("DoubleClick", CopySelectedTemplate)
LV.OnEvent("Click", LoadSelectedTemplate)

; Add the new editable box for template content
contentEdit := MyGui.Add("Edit", "x222 y25 w370 h340 vTemplateContent Background000000 cFFFFFF")

btc := "55c2da"  ;"0A9186"     ; Button color
bfc := "050505"     ; Button font color

; Add buttons
GetT_GUI_button := MyGui.Add("Button", "x10 y370 w60 h20", "Copy"), GetT_GUI_button.OnEvent("Click", CopySelectedTemplate), GetT_GUI_button.SetColor(btc, bfc,, bfc, 9)
GetT_GUI_button := MyGui.Add("Button", "x+10 w60 h20", "Refresh"), GetT_GUI_button.OnEvent("Click", RefreshTemplateList), GetT_GUI_button.SetColor(btc, bfc,, bfc, 9)
GetT_GUI_button := MyGui.Add("Button", "x+10 w60 h20", "Add New"), GetT_GUI_button.OnEvent("Click", CreateNewTemplate), GetT_GUI_button.SetColor(btc, bfc,, bfc, 9)
GetT_GUI_button := MyGui.Add("Button", "x+10 w60 h20", "Delete"), GetT_GUI_button.OnEvent("Click", DeleteSelectedTemplate), GetT_GUI_button.SetColor(btc, bfc,, bfc, 9)
GetT_GUI_button := MyGui.Add("Button", "x+10 w60 h20", "Reload"), GetT_GUI_button.OnEvent("Click", (*) => Reload()), GetT_GUI_button.SetColor(btc, bfc,, bfc, 9)
GetT_GUI_button := MyGui.Add("Button", "x+10 w60 h20", "Save"), GetT_GUI_button.OnEvent("Click", SaveTemplateContent), GetT_GUI_button.SetColor(btc, bfc,, bfc, 9)
GetT_GUI_button := MyGui.Add("Button", "x+10 w80 h20", "Open Folder"), GetT_GUI_button.OnEvent("Click", (*) => Run(A_ScriptDir "\Templates")), GetT_GUI_button.SetColor(btc, bfc,, bfc, 9)

; Function to refresh the template list
RefreshTemplateList(*) {
    LV.Delete()
    Loop Files, templateDir "\*.txt"
        LV.Add(, StrReplace(A_LoopFileName, ".txt"))
}

; Function to copy selected template content to clipboard
CopySelectedTemplate(*) {
    if (rowNumber := LV.GetNext()) {
        fileName := LV.GetText(rowNumber, 1) . ".txt"
        filePath := templateDir "\" fileName
        try {
            content := FileRead(filePath)
            A_Clipboard := content
            if !ClipWait(1)
                throw Error("Failed to set clipboard")
            ToolTip("Template copied to clipboard!")
            SetTimer () => ToolTip(), -2000  ; Remove tooltip after 2 seconds
        } catch as err {
            MsgBox("Error: " err.Message, "Template Error", 16)
        }
    }
}

; Function to load selected template content into the edit box
LoadSelectedTemplate(*) {
    if (rowNumber := LV.GetNext()) {
        fileName := LV.GetText(rowNumber, 1) . ".txt"
        filePath := templateDir "\" fileName
        try {
            content := FileRead(filePath)
            contentEdit.Value := content
        } catch as err {
            MsgBox("Error loading template: " err.Message, "Template Error", 16)
        }
    }
}

; Function to save the content of the edit box to the selected template file
SaveTemplateContent(*) {
    if (rowNumber := LV.GetNext()) {
        fileName := LV.GetText(rowNumber, 1) . ".txt"
        filePath := templateDir "\" fileName
        try {
            FileDelete(filePath)
            FileAppend(contentEdit.Value, filePath)
            MsgBox("Template saved successfully!", "Success")
        } catch as err {
            MsgBox("Error saving template: " err.Message, "Error", 16)
        }
    } else {
        MsgBox("Please select a template to save.", "Error", 16)
    }
}

; Function to create a new template file
CreateNewTemplate(*) {
    NewTemplateGui := Gui()
    NewTemplateGui.OnEvent("Close", (*) => NewTemplateGui.Destroy())
    NewTemplateGui.Title := "Create New Template"
    NewTemplateGui.BackColor := "202020"
    NewTemplateGui.SetFont("s10 cFFFFFF", "Cascadia Code")

    NewTemplateGui.Add("Text",, "Template Name:")
    nameEdit := NewTemplateGui.Add("Edit", "w200 vTemplateName Background050505")
    NewTemplateGui.Add("Text", "xm", "Template Content:")
    contentEdit := NewTemplateGui.Add("Edit", "r10 w300 vTemplateContent Background000000")

    NewTemplateGui.Add("Button", "w100 Default", "Save").OnEvent("Click", (*) => SaveNewTemplate(NewTemplateGui, nameEdit, contentEdit))
    NewTemplateGui.Show()
}

; Function to save a new template file
SaveNewTemplate(gui, nameEdit, contentEdit) {
    templateName := nameEdit.Value
    templateContent := contentEdit.Value

    if (templateName != "" and templateContent != "") {
        filePath := templateDir "\" templateName ".txt"
        try {
            FileAppend(templateContent, filePath)
            gui.Destroy()
            RefreshTemplateList()
            ; CreateHotstrings()
        } catch as err {
            MsgBox("Error saving template: " err.Message, "Error", 16)
        }
    } else {
        MsgBox("Please enter both template name and content.", "Error", 16)
    }
}

; Function to delete the selected template
DeleteSelectedTemplate(*) {
    if (rowNumber := LV.GetNext()) {
        fileName := LV.GetText(rowNumber, 1) . ".txt"
        filePath := templateDir "\" fileName
        result := MsgBox("Are you sure you want to delete this template?", "Confirm Delete", 4)
        if (result == "Yes") {
            try {
                FileDelete(filePath)
                RefreshTemplateList()
                ; CreateHotstrings()
                contentEdit.Value := ""  ; Clear the content edit box
                MsgBox("Template deleted successfully!", "Success")
            } catch as err {
                MsgBox("Error deleting template: " err.Message, "Error", 16)
            }
        }
    } else {
        MsgBox("Please select a template to delete.", "Error", 16)
    }
}

; Function to set up text shortcuts
; CreateHotstrings() {
;     Hotstring("Reset")
;     Loop Files, templateDir "\*.txt" {
;         triggerName := StrReplace(A_LoopFileName, ".txt")
;         Hotstring(":*:" triggerName, InsertTemplate.Bind(A_LoopFilePath))
;     }
; }

; Function to insert template content
InsertTemplate(filePath, *) {
    try {
        content := FileRead(filePath)
        A_Clipboard := content
        if !ClipWait(1)
            throw Error("Failed to set clipboard")
        Send "^v"
    } catch as err {
        MsgBox("Error with template: " err.Message, "Template Error", 16)
    }
}

; Initial setup
; CreateHotstrings()
RefreshTemplateList()

; Refresh hotstrings every 30 seconds
; SetTimer(CreateHotstrings, 30000)
}
MButton::ShowGui()

OnEnter(*){
    Search()
}

ShowGui(){
    A_Clipboard := ""
    Send("^c")
    ClipWait(1, 1)
    MyGui.Show("w600 h400")
    Sleep(500)
    ControlSend("^a^v", "Edit1", "OneGui")
    Sleep(500)
    A_Clipboard := ""
}

v1Doc(*){
    allclips := ClipboardAll()
    ClipSave()
    RunWait("https://www.autohotkey.com/docs/v1/lib/")
}

Adddate(*){
    WinSetAlwaysOnTop(true)
    addrsub := InputBox("Enter no of days to add", , "w220 h150").Value
    if addrsub != ""
    {
        m1d := A_Now
        m1d += addrsub, "Days"
        Nday := FormatTime(m1d, "dd-MMM-yyyy")
        Send(Nday " ")
    }
}

v2Doc(*){
    allclips := ClipboardAll()
    ClipSave()
    RunWait("https://www.autohotkey.com/docs/v2/lib/")
    A_Clipboard := allclips
}

Ra(*){
    ReloadScript(A_MyDocuments  . "\AutoHotkey\Default_Folder\ScreenClipping.ahk")
    ReloadScript(A_MyDocuments  . "\AutoHotkey_V2\v2Automation.ahk")
    ReloadScript(A_MyDocuments  . "\AutoHotkey_V2\AutoHotkey_version_2\projects\Menu\Version 2\Dark Mode v2\ActionMenuV2.ahk")
    ToolTip "Reloading`nScreenClipping - v2Automation - ActionMenuV2 - OneGUI"
    Sleep 1500
    Reload()
}

close_working(*){
    windows := ["ahk_class Notepad++", "ahk_exe chrome.exe", "ahk_exe Code.exe", "ahk_exe SciTE.exe"]
    for window in windows {
        if WinExist(window) {
            WinActivate()
            WinClose()
        }
    }
}

stock_check(*){
    Run("https://www.screener.in/")
    Run("https://www.google.com/search?q=NSE: TATAMOTORS")
    Run("https://www.google.com/search?q=NSE: CANBK")
    Run("https://www.google.com/search?q=NSE: IRCTC")
    Run("https://www.google.com/search?q=NSE: HAL")
    Run("https://www.google.com/search?q=NSE: adanigreen")
}

Search(*){
    searchQuery := Ed.Text  ; Use the control object directly

    ; Check if the input field is empty
    if (searchQuery = "") {
        ToolTip("Please enter a search query")
        SetTimer(() => ToolTip(), -3000)  ; Hide tooltip after 3 seconds
        return
    }

    isAnySelected := false ; Check if any checkbox is selected

    Loop 23 {
        if (MyGui["C" A_Index].Value) {
            isAnySelected := true
            break
        }
    }
    ; If no checkbox is selected, show a message to the user
    if (!isAnySelected) {
        ToolTip "Please select at least one CheckBox to search."
        SetTimer () => ToolTip(), -5000
        return
    }
    if MyGui["C1"].Value
        Run("https://duckduckgo.com/?q=" searchQuery)
    if MyGui["C2"].Value
        Run("https://www.google.com/search?q=" searchQuery)
    if MyGui["C3"].Value
        Run("https://www.youtube.com/results?search_query=" searchQuery)
    if MyGui["C4"].Value
        Run("https://www.reddit.com/search/?q=" searchQuery)
    if MyGui["C5"].Value
        Run("https://www.amazon.in/s?k=" searchQuery "&ref=nb_sb_noss")
    if MyGui["C6"].Value
        Run("https://www.flipkart.com/search?q=" searchQuery)
    if MyGui["C7"].Value
        Run("https://www.wolframalpha.com/input/?i=" searchQuery)
    if MyGui["C8"].Value
        Run("https://www.reddit.com/r/learnprogramming/search/?q=" searchQuery)
    if MyGui["C9"].Value
        Run("https://www.reddit.com/r/AutoHotkey/search/?q=" searchQuery)
    if MyGui["C10"].Value
        Run("https://www.reddit.com/r/Excel/search/?q=" searchQuery "&restrict_sr=1&sr_nsfw=")
    if MyGui["C11"].Value
        Run("https://www.reddit.com/r/vbscript/search/?q=" searchQuery "&restrict_sr=1&sr_nsfw=")
    if MyGui["C12"].Value
        Run("https://www.reddit.com/r/learnpython/search/?q=" searchQuery "&restrict_sr=1&sr_nsfw=")
    if MyGui["C13"].Value
        Run("https://www.reddit.com/r/Batch/search/?q=" searchQuery "&restrict_sr=1&sr_nsfw=")
    if MyGui["C14"].Value
        Run("https://www.reddit.com/r/PowerShell/search/?q=" searchQuery "&restrict_sr=1&sr_nsfw=")
    if MyGui["C15"].Value
        Run("https://www.reddit.com/r/AutomateYourself/search/?q=" searchQuery "&restrict_sr=1&sr_nsfw=")
    if MyGui["C16"].Value
        Run("https://www.instagram.com/" searchQuery "/")
    if MyGui["C17"].Value
        Run("https://twitter.com/search?q=" searchQuery)
    if MyGui["C18"].Value
        Run("https://www.linkedin.com/search/results/all/?keywords=" searchQuery)
    if MyGui["C19"].Value {
        Run("https://chat.openai.com/auth/login")
        WinWait("ChatGPT - Google Chrome")
        BrowserTabFinder("ChatGPT - Google Chrome")
        Sleep(2000)
        Send(searchQuery)
        Sleep(1000)
        Send("{Enter}")
    }
    if MyGui["C20"].Value {
        Run("https://bard.google.com/chat")
        WinWait("Gemini - Google Chrome")
        BrowserTabFinder("Gemini - Google Chrome")
        Sleep(2000)
        Send(searchQuery)
        Sleep(2000)
        Send("{Enter}")
    }
    if MyGui["C21"].Value {
        Run("https://www.autohotkey.com/docs/v1/lib/" searchQuery ".htm")
    }
    if MyGui["C22"].Value {
        Run("https://www.autohotkey.com/docs/v2/lib/" searchQuery ".htm")
        Run("https://www.reddit.com/search/?q=flair:v2_Script_Help+" searchQuery "&type=link")
    }
    if MyGui["C23"].Value {
        Run("https://www.quora.com/search?q=" searchQuery)
    }

    ; Clear all checkboxes
    Loop 23 {
        MyGui["C" A_Index].Value := false
    }
}

ClipSave(){
    A_Clipboard := ""
    ClipWait(0)
    myclip := A_Clipboard 
    SendText(myclip)
}

#HotIf WinActive("ahk_exe EXCEL.EXE")
RCtrl::RButton
```
</details>
<br>

## Any Selected Window Resizer GUI:
![Description of the image](My_AHK_Project_Snaps/Window_Resizer_GUI.png "Window_Resizer_GUI")


<details>
<summary>Click to expand/collapse the code</summary>

```AutoHotkey
;;; =========== Window Managment ===========================
class WMove {
    static screenWidth := 2560
    static screenHeight := 1440
    static sectionWidth := WMove.screenWidth // 4
    static sectionHeight := WMove.screenHeight // 2
    static halfWidth := WMove.screenWidth // 2
    static halfHeight := WMove.screenHeight // 2

    static Move(x, y, width, height, winTitle := "A") {
        WinMinimize(winTitle)
        WinMove(x, y, width, height, winTitle)
        WinRestore(winTitle)
        WinActivate(winTitle)
        if WinExist("WMove Window Manager") {
            WinActivate()
        }
    }

    ; 4x2 grid functions
    static Q1() {
        WMove.Move(0, 0, WMove.sectionWidth, WMove.sectionHeight)
    }

    static Q2() {
        WMove.Move(WMove.sectionWidth, 0, WMove.sectionWidth, WMove.sectionHeight)
    }

    static Q3() {
        WMove.Move(WMove.sectionWidth * 2, 0, WMove.sectionWidth, WMove.sectionHeight)
    }

    static Q4() {
        WMove.Move(WMove.sectionWidth * 3, 0, WMove.sectionWidth, WMove.sectionHeight)
    }

    static Q5() {
        WMove.Move(0, WMove.sectionHeight, WMove.sectionWidth, WMove.sectionHeight)
    }

    static Q6() {
        WMove.Move(WMove.sectionWidth, WMove.sectionHeight, WMove.sectionWidth, WMove.sectionHeight)
    }

    static Q7() {
        WMove.Move(WMove.sectionWidth * 2, WMove.sectionHeight, WMove.sectionWidth, WMove.sectionHeight)
    }

    static Q8() {
        WMove.Move(WMove.sectionWidth * 3, WMove.sectionHeight, WMove.sectionWidth, WMove.sectionHeight)
    }

    ; 2x2 grid functions
    static H1() {
        WMove.Move(0, 0, WMove.halfWidth, WMove.halfHeight)
    }

    static H2() {
        WMove.Move(WMove.halfWidth, 0, WMove.halfWidth, WMove.halfHeight)
    }

    static H3() {
        WMove.Move(0, WMove.halfHeight, WMove.halfWidth, WMove.halfHeight)
    }

    static H4() {
        WMove.Move(WMove.halfWidth, WMove.halfHeight, WMove.halfWidth, WMove.halfHeight)
    }

    ; Center function
    static Center() {
        WinMinimize("WMove Window Manager")
        winTitle := WinGetTitle("A")
        WinActivate(winTitle)
        WinGetPos(&x, &y, &width, &height, winTitle)
        newX := (A_ScreenWidth / 2) - (width / 2)
        newY := (A_ScreenHeight / 2) - (height / 2)
        
        WinMove(newX, newY, , , winTitle)
        WinActivate(winTitle)
        if WinExist("WMove Window Manager") {
            WinActivate()
        }
    }

    ; Function to show GUI
    static ShowGUI() {
        if WinExist("WMove Window Manager") {
            WinShow()
            WinActivate()
        } else {
            WMoveGUI.Show()
        }
    }
}

class WMoveGUI {
    static guiObj := {}
    
    static Show() {
        if (this.guiObj.HasProp("Hwnd")) {
            this.guiObj.Show()
            return
        }

        this.guiObj := Gui()
        this.guiObj.Title := "Window Resizer GUI"
        this.guiObj.Opt("+AlwaysOnTop -Sysmenu")
        this.guiObj.BackColor := "0x000000"  ; Dark background

        ; 4x2 Grid
        this.guiObj.Add("Text", "x10 y10 w220 c0xff0909", "4x2 Grid")
        this.AddButton("Q1", 10, 30, 50, 30)
        this.AddButton("Q2", 65, 30, 50, 30)
        this.AddButton("Q3", 120, 30, 50, 30)
        this.AddButton("Q4", 175, 30, 50, 30)
        this.AddButton("Q5", 10, 65, 50, 30)
        this.AddButton("Q6", 65, 65, 50, 30)
        this.AddButton("Q7", 120, 65, 50, 30)
        this.AddButton("Q8", 175, 65, 50, 30)
        
        ; 2x2 Grid
        this.guiObj.Add("Text", "x10 y110 w220 c0xff0909", "2x2 Grid")
        this.AddButton("H1", 10, 135, 105, 30)
        this.AddButton("H2", 120, 135, 105, 30)
        this.AddButton("H3", 10, 170, 105, 30)
        this.AddButton("H4", 120, 170, 105, 30)
        
        ; Center Button
        this.AddButton("CENTER", 10, 230, 215, 30)
        
        this.guiObj.Show("w235")
    }
    
    static AddButton(name, x, y, w, h) {
        btn := this.guiObj.Add("Button", Format("x{} y{} w{} h{}", x, y, w, h), name)
        btn.OnEvent("Click", (*) => WMove.%name%())
        this.SetButtonColors(btn)
    }

    static SetButtonColors(btn) {
        btn.Opt("+Background333333 +c0xFFFFFF")  ; Dark gray background, white text
    }
}
```
</details>

<br>


## 💡Action Menu:
![Description of the image](My_AHK_Project_Snaps/Action_Menu.png "Action_Menu")


<details>
<summary>Click to expand/collapse the code</summary>

```AutoHotkey
#Requires AutoHotkey v2.0+
#SingleInstance Force
TraySetIcon A_ScriptDir "\icons\Menu.ico"
~!Space::Reload

; ~Escape::ExitApp
;;========================
global iconpath := A_ScriptDir . "\icons\"
; MsgBox path

; Create the main menu
OneMenu := Menu()
Online_Shopping := Menu() 
(item := "Electronics", Online_Shopping.Add(item, (*) => Electronics()), Online_Shopping.SetIcon(item, "Shell32.dll", 266))
(item := "Fashion", Online_Shopping.Add(item, (*) => Fashion()), Online_Shopping.SetIcon(item, "Shell32.dll", 266))
(item := "Home && Furniture", Online_Shopping.Add(item, (*) => Home_furniture()), Online_Shopping.SetIcon(item, "Shell32.dll", 266))
(item := "Groceries", Online_Shopping.Add(item, (*) => Groceries()), Online_Shopping.SetIcon(item, "Shell32.dll", 266))
(item := "Beauty && Wellness", Online_Shopping.Add(item, (*) => Beauty_Wellness()), Online_Shopping.SetIcon(item, "Shell32.dll", 266))
(item := "Books", Online_Shopping.Add(item, (*) => Books()), Online_Shopping.SetIcon(item, "Shell32.dll", 266))
(item := "Sports && Fitness", Online_Shopping.Add(item, (*) => Sports_Fitness()), Online_Shopping.SetIcon(item, "Shell32.dll", 266))
(item := "Toys && Baby Products", Online_Shopping.Add(item, (*) => Toys_Baby_Products()), Online_Shopping.SetIcon(item, "Shell32.dll", 266))

news := Menu()
(item := "World News", news.Add(item, (*) => World_News()), news.SetIcon(item, "C:\Program Files\Google\Chrome\Application\chrome.exe", 1))
(item := "Social Media News", news.Add(item, (*) => Social_Media_News()), news.SetIcon(item, "C:\Program Files\Google\Chrome\Application\chrome.exe", 1))
(item := "General News", news.Add(item, (*) => general_news()), news.SetIcon(item, "C:\Program Files\Google\Chrome\Application\chrome.exe", 1))
(item := "Tech News", news.Add(item, (*) => Technology_News()), news.SetIcon(item, "C:\Program Files\Google\Chrome\Application\chrome.exe", 1))
(item := "Financial News", news.Add(item, (*) => Financial_News()), news.SetIcon(item, "C:\Program Files\Google\Chrome\Application\chrome.exe", 1))
(item := "Science News", news.Add(item, (*) => Science_News()), news.SetIcon(item, "C:\Program Files\Google\Chrome\Application\chrome.exe", 1))

Web_Search := Menu()
(item := "Google`tAlt+g", Web_Search.Add(item, (*) => google_search()), Web_Search.SetIcon(item, iconpath . "gg.png"))
(item := "News", Web_Search.Add(item, (*) => google_news()), Web_Search.SetIcon(item, iconpath . "news.png"))
(item := "Youtube`tAlt+y", Web_Search.Add(item, (*) => yt_search()), Web_Search.SetIcon(item, iconpath . "yt.png"))
(item := "Google Maps`tAlt+m", Web_Search.Add(item, (*) => maps()), Web_Search.SetIcon(item, iconpath . "gm.png"))
(item := "Find in Social Media", Web_Search.Add(item, (*) => Social_Media()), Web_Search.SetIcon(item, "Shell32.dll", 171))

google_search(){
Runurl("https://google.com/search?q=","https://google.com/")
}
google_news(){
    Runurl("https://news.google.com/search?q=","https://news.google.com/")
}
yt_search(){
Runurl("https://www.youtube.com/results?search_query=","https://www.youtube.com")
}
maps(){
Runurl("https://www.google.com/maps/search/","https://www.google.com/maps")
}

!g::google_search()
!y::yt_search()
!m::maps()

; Create and populate the format submenu
formatMenu := Menu()
(item := "lower case`tAlt+L", formatMenu.Add(item, (*) => format_text("L")), formatMenu.SetIcon(item, "shell32.dll", 76))
(item := "UPPER CASE`tAlt+U", formatMenu.Add(item, (*) => format_text("U")), formatMenu.SetIcon(item, "shell32.dll", 76))
(item := "Title Case`tAlt+T", formatMenu.Add(item, (*) => format_text("T")), formatMenu.SetIcon(item, "shell32.dll", 76))
(item := "Clean Lines/Space`tAlt+S", formatMenu.Add(item, (*) => remove_excess_space()), formatMenu.SetIcon(item, "shell32.dll", 76))

; Create and populate the wrap submenu
wrapMenu := Menu()
(item := '"Double Quotes"`tAlt+`'', wrapMenu.Add(item, (*) => wrap('"', '"')), wrapMenu.SetIcon(item, "shell32.dll", 134))
(item := "'Single Quotes'`tAlt+5", wrapMenu.Add(item, (*) => wrap("'", "'")), wrapMenu.SetIcon(item, "shell32.dll", 134))
(item := "(Parentheses)`tAlt+9", wrapMenu.Add(item, (*) => wrap("(", ")")), wrapMenu.SetIcon(item, "shell32.dll", 134))
(item := "[Square Brackets]`tAlt+[", wrapMenu.Add(item, (*) => wrap("[", "]")), wrapMenu.SetIcon(item, "shell32.dll", 134))
(item := "{Curly Brackets}`tCtrl+Alt+[", wrapMenu.Add(item, (*) => wrap("{U+007B}", "{U+007D}")), wrapMenu.SetIcon(item, "shell32.dll", 134))

Systemapps := Menu()
(item := "Bluetooth", Systemapps.Add(item, (*) => Run("ms-settings:bluetooth")), Systemapps.SetIcon(item, iconpath . "bt.png"))
(item := "List All Apps", Systemapps.Add(item, (*) => Run("shell:appsfolder")), Systemapps.SetIcon(item, "Shell32.dll", 23))
(item := "Uninstaller", Systemapps.Add(item, (*) => Run("appwiz.cpl")), Systemapps.SetIcon(item, "Shell32.dll", 208))
(item := "Manage Users", Systemapps.Add(item, (*) => Run("netplwiz")), Systemapps.SetIcon(item, "Shell32.dll", 112))
(item := "powershell", Systemapps.Add(item, (*) => Run("powershell")), Systemapps.SetIcon(item, "PowerShell.exe", 1))
Systemapps.Add()  ; This line adds a separator
(item := "Shutdown", Systemapps.Add(item, (*) => Shutdown(1)), Systemapps.SetIcon(item, "Shell32.dll", 28))
(item := "Restart", Systemapps.Add(item, (*) => Shutdown(2)), Systemapps.SetIcon(item, "Shell32.dll", 239))
(item := "Hibernate", Systemapps.Add(item, (*) => Run("rundll32.exe powrprof.dll,SetSuspendState 0,1,0")), Systemapps.SetIcon(item, "Shell32.dll", 240))

Daily_Tools := Menu()
(item := "Bulk File Creation", Daily_Tools.Add(item, (*) => Bulknewfile()), Daily_Tools.SetIcon(item, "Shell32.dll", 251))
(item := "Bulk Folder Creation", Daily_Tools.Add(item, (*) => Bulknewfolder()), Daily_Tools.SetIcon(item, "Shell32.dll", 299))
(item := "Strong Password Generator", Daily_Tools.Add(item, (*) => GenerateAndDisplayPasswords()), Daily_Tools.SetIcon(item, "Shell32.dll", 48))
(item := "Percentage Calc", Daily_Tools.Add(item, (*) => ShowPercentageCalculator()), Daily_Tools.SetIcon(item, iconpath . "calc.png"))
(item := "URL Virus Scanner ", Daily_Tools.Add(item, (*) => checkurl_in_virustotal()), Daily_Tools.SetIcon(item, "Shell32.dll", 245))
(item := "Whatsapp Direct Message", Daily_Tools.Add(item, (*) => wa_send()), Daily_Tools.SetIcon(item, iconpath . "wa.png"))
(item := "Copy File content", Daily_Tools.Add(item, (*) => CopyFileContent()), Daily_Tools.SetIcon(item, "Shell32.dll", 69))

submenu := Menu()
(item := "Fix spelling && grammer", submenu.Add(item, (*) => OpenChatGPTAndPaste("Please correct any spelling and grammatical errors in the following text, ensuring proper punctuation and sentence structure.")), submenu.SetIcon(item, iconpath . "chatgptnew.png"))
(item := "Rewrite For Clarity", submenu.Add(item, (*) => OpenChatGPTAndPaste("Rewrite the following text to improve clarity and readability, maintaining the original meaning but making it easier to understand. Also mention what changes have made from the old and new Text")), submenu.SetIcon(item, iconpath . "chatgptnew.png"))
(item := "Explain this", submenu.Add(item, (*) => OpenChatGPTAndPaste("Please provide a detailed explanation of the concept or information presented in the following text, breaking it down for easier understanding.")), submenu.SetIcon(item, iconpath . "chatgptnew.png"))
(item := "Find action items", submenu.Add(item, (*) => OpenChatGPTAndPaste("Identify and list any specific actions, tasks, or next steps mentioned or implied in the following text.")), submenu.SetIcon(item, iconpath . "chatgptnew.png"))
(item := "Summarize", submenu.Add(item, (*) => OpenChatGPTAndPaste("Provide a concise summary of the main points and key ideas from the following text.")), submenu.SetIcon(item, iconpath . "chatgptnew.png"))
submenu.Add()
(item := "Make Shorter", submenu.Add(item, (*) => OpenChatGPTAndPaste("Condense the following text, preserving the key points while reducing overall length.")), submenu.SetIcon(item, iconpath . "chatgptnew.png"))
(item := "Make longer", submenu.Add(item, (*) => OpenChatGPTAndPaste("Expand on the given text, adding more details, examples, or explanations to create a more comprehensive version.")), submenu.SetIcon(item, iconpath . "chatgptnew.png"))
(item := "Change Tone - Simpler", submenu.Add(item, (*) => OpenChatGPTAndPaste("Rewrite the following text using simpler language and concepts. Make it accessible to a general audience, avoiding technical terms and complex ideas. Aim for a version that could be easily understood by someone with basic reading skills.")), submenu.SetIcon(item, iconpath . "chatgptnew.png"))
(item := "Change Tone - Casual", submenu.Add(item, (*) => OpenChatGPTAndPaste("Rewrite the given text in a more casual, conversational tone. Use informal language, contractions, and a friendly style as if you're talking to a friend. Include colloquialisms where appropriate, but avoid slang that might be too region-specific or obscure.")), submenu.SetIcon(item, iconpath . "chatgptnew.png"))
(item := "Change Tone - Professional", submenu.Add(item, (*) => OpenChatGPTAndPaste("Rewrite the following text to adopt a more professional and formal tone suitable for a business context.")), submenu.SetIcon(item, iconpath . "chatgptnew.png"))
submenu.Add()
(item := "Argument Booster`t- Advanced", submenu.Add(item, (*) => OpenChatGPTAndPaste("Strengthen The Given Argument With Additional Evidence Or Reasoning. Present Opposing Views For A Comprehensive Analysis. Incorporate Relevant, Credible Research Findings. Anticipate And Respond To Potential Counterarguments. Use Analogies To Clarify Complex Concepts.")), submenu.SetIcon(item, iconpath . "chatgpt.png"))
(item := "Language Polisher`t- Advanced", submenu.Add(item, (*) => OpenChatGPTAndPaste("Review The Following Text For Spelling, Punctuation, And Grammatical Errors. Check For Inconsistencies And Improve Overall Coherence. Enhance Sentence Structure And Flow. Rewrite For Better Understanding While Preserving Meaning. Replace Complex Or Field-Specific Terms With Simpler Alternatives. Adjust Structure And Formatting To Increase Engagement.")), submenu.SetIcon(item, iconpath . "chatgpt.png"))
(item := "Content Enhancer`t- Advanced", submenu.Add(item, (*) => OpenChatGPTAndPaste("Enhance The Following Content By Emphasizing Crucial Information For Clarity. Verify Accuracy Using Reliable Sources And Include Supporting References. Ensure Statistical Information Is Current. Condense Main Ideas Into A Brief Overview. Provide Clear Explanations Suitable For A General Audience. Highlight Specific Tasks Or Next Steps. Add Relevant Stories, Interactive Elements, And Practical Illustrations. Emphasize Positive Outcomes Or Advantages.")), submenu.SetIcon(item, iconpath . "chatgpt.png"))
(item := "Length Optimizer`t- Advanced", submenu.Add(item, (*) => OpenChatGPTAndPaste("Optimize The Length Of The Following Text. [Shorten/Expand] While [Maintaining Essential Information/Adding Relevant Details]. [Remove Unnecessary Content For Brevity/Provide More Detailed Explanations In Key Areas].")), submenu.SetIcon(item, iconpath . "chatgpt.png"))
(item := "Structure Refiner`t- Advanced", submenu.Add(item, (*) => OpenChatGPTAndPaste("Improve The Structure Of The Following Content. Remove Repetitive Elements For Focus. Suggest Placements For Helpful Visuals. Enhance Design Elements For Appeal. Reorganize For Easier Reading And Engagement. Ensure Logical Flow With Smooth Transitions. Implement Appropriate Headings, Bullets, And Other Formatting To Improve Readability. Insert Relevant Section Titles And Subtitles.")), submenu.SetIcon(item, iconpath . "chatgpt.png"))
(item := "Tone Tuner`t- Advanced", submenu.Add(item, (*) => OpenChatGPTAndPaste("Adjust The Tone Of The Following Text To Be [Formal/Casual/Business-Appropriate/Etc.]. [Include Light-Hearted Elements/Adopt A More Serious Style] As Needed. Modify To Reflect [Specific Company Personality Or Values]. Tailor The Content To Connect With [Target Audience].")), submenu.SetIcon(item, iconpath . "chatgpt.png"))
(item := "Style Enhancer`t- Advanced", submenu.Add(item, (*) => OpenChatGPTAndPaste("Enhance The Style Of The Following Text. Rewrite Sentences To Emphasize Active Voice. Adjust For Precision And Clarity, Especially In Technical Contexts. Vary Sentence Length To Improve Rhythm And Flow. Incorporate Figurative Language Like Metaphors And Similes To Enhance Description. Use Formatting Techniques To Highlight Important Terms Or Phrases.")), submenu.SetIcon(item, iconpath . "chatgpt.png"))

(item := "Ask ChatGPT", OneMenu.Add(item, submenu), OneMenu.SetIcon(item, iconpath . "chatgptnew.png"))
(item := "Web Search", OneMenu.Add(item, Web_Search), OneMenu.SetIcon(item, "shell32.dll", 14))
(item := "Unified News Search", OneMenu.Add(item, news), OneMenu.SetIcon(item, "Shell32.dll", 168))
(item := "Online Shopping", OneMenu.Add(item, Online_Shopping), OneMenu.SetIcon(item, "Shell32.dll", 266))
(item := "Format Text", OneMenu.Add(item, formatMenu), OneMenu.SetIcon(item, "shell32.dll", 76))
(item := "Wrap Text", OneMenu.Add(item, wrapMenu), OneMenu.SetIcon(item, "shell32.dll", 134))
OneMenu.Add()
(item := "System", OneMenu.Add(item, Systemapps), OneMenu.SetIcon(item, "shell32.dll", 15))
(item := "Daily_Tools", OneMenu.Add(item, Daily_Tools), OneMenu.SetIcon(item, "Imageres.dll", 36))

;;===========================================================================
; Hotkey to show the main menu
#HotIf not WinActive("ahk_class CabinetWClass")
RButton:: {
    startTime := A_TickCount
    KeyWait "RButton", "T0.5"
    elapsedTime := A_TickCount - startTime
    
    if (elapsedTime >= 500) {
        callmenu()  ; Replace with the actual function or script you want to call
    } else {
        if (A_PriorKey == "RButton") {
            Send "{RButton}"
        }
    }
}
#HotIf
; #w::callmenu()


callmenu(){
copy2clip()
global Search_text := A_Clipboard
    SetPreferredAppMode()
    FlushMenuThemes()
OneMenu.Show()
}

; Hotkeys for text formatting
!l:: format_text("L")  ; Alt+L: Convert to lowercase
!u:: format_text("U")  ; Alt+U: Convert to UPPERCASE
!T:: format_text("T")  ; Alt+T: Convert to Title Case
!s:: remove_excess_space()  ; Alt+S: Clean excess spaces and lines

; Hotkeys for text wrapping
!':: wrap('"', '"')  ; Alt+': Wrap with double quotes
!5:: wrap("'", "'")    ; Alt+5: Wrap with percent signs
!9:: wrap("(", ")")    ; Alt+9: Wrap with parentheses
![:: wrap("[", "]")    ; Alt+[: Wrap with square brackets
~^![:: wrap("{U+007B}", "{U+007D}")    ; Ctrl+Alt+[: Wrap with Curly Brackets

copy2clip() {
bak := ClipboardAll()
A_Clipboard := ""
Send("^c")
if (ClipWait(1, 1)) {
    return A_Clipboard
} else 
; ToolTip("Couldn't put text into Clipboard.",)
; SetTimer () => ToolTip(), -5000
A_Clipboard := bak
}
; Function to format text case (lower, UPPER, Title)
format_text(n) {
A_Clipboard := copy2clip()
A_Clipboard := Format("{:" . n . "}", A_Clipboard)
Send "^v"
}
; Function to remove excess spaces and normalize line breaks
remove_excess_space() {
A_Clipboard := ""
Send("^c")
ClipWait(1)

text := A_Clipboard
text := RegExReplace(text, "\R{2,}", "`r`n`r`n")  ; Reduce multiple line breaks to double
text := RegExReplace(text, "([^\r\n]) {2,}", "$1 ")  ; Remove excess spaces between words
text := RegExReplace(text, "^ +| +$", "", , -1)  ; Trim leading/trailing spaces from each line
text := Trim(text)  ; Trim entire text

A_Clipboard := text
Send("^v")
}
; Function to wrap selected text with specified characters
wrap(x, y, z := 100) {
Send "^x" . Sleep(z) . x . Sleep(z) . "^v" . Sleep(z) . y
}

; ===>> create bulk folder by 'md foldername' using .bat file method
Bulknewfolder(){
Run "Notepad" 
WinWaitActive "Untitled - Notepad"
A_Clipboard := "md folder_name1`nmd folder_name2`nmd folder_name3`nmd folder_name4`nmd folder_name5`nmd folder_name6`nmd folder_name7"
Sendw("^v", 1500)
Sendw("^s", 1500)
sendw("create_bulk_folders.bat{Tab}", 1500)
sendw("{Down 2}{Enter}", 0)
}
; ===>> create bulk files by 'echo.> filename.txt' using .bat file method
Bulknewfile(){
Run 'Notepad'
WinWaitActive 'Untitled - Notepad'
A_Clipboard := 'echo off`necho.>filename1.xls`necho.>hai2.txt`necho.>filename.docx'
Sendw('^v', 1500)
Sendw('^s', 1500)
Sendw('create_bulk_new_files.bat{Tab}', 1500)
send('{Down 2}{Enter}')
}

sendw(key, delay:=1000, times := 1) {
loop times {
    SendEvent key
    Sleep delay
}
}
OpenChatGPTAndPaste(prompt) {
if BrowserTabFinder('ChatGPT') {
    Sleep 2000
    click_chatgpt_inputarea('ChatGPT')
    A_Clipboard := prompt . ' > ' . Search_text
    Send '^v' . "{Enter}"
} else {
    Run "https://chat.openai.com/"
    WinWaitActive 'ChatGPT'
    Sleep 2000 ; Wait for 2 seconds
    A_Clipboard := prompt . ' > ' . Search_text
    Send '^v' . "{Enter}"
}
}
;;; ===============================================
click_chatgpt_inputarea(title) {
if WinExist(title) {
    WinGetPos ,,&W, &H, "A"        
    W := W / 2
    H := H - 75
    ; Move the mouse and click
    MouseMove W, H
    Sleep 500
    Click
    Sleep 500
}
}
;;; ===============================================
GenerateAndDisplayPasswords() {
static charSets := Map(
    "l", "abcdefghijklmnopqrstuvwxyz",
    "u", "ABCDEFGHIJKLMNOPQRSTUVWXYZ",
    "n", "0123456789",
    "s", "~!@#$%^&*()_+-=[]{}|;:,.<>?"
)

length := InputBox("Enter the desired password length?`n(must be a multiple of 4, like 4, 8, 12, 16, 20 etc.):`n`nFUN FACT: The longest password ever used was 1,273 characters long!`n`nADVICE: Longer passwords are harder to crack.", "Password Generator", "w380 h200").Value
if (length == "" || !IsInteger(length) || length < 4 || Mod(length, 4) != 0) {
    MsgBox("Please enter a valid positive integer that is a multiple of 4.", "Invalid Input", 48)
    return
}

charPerType := length // 4
passwords := []

Loop 10 {
    password := ""
    for _, chars in charSets {
        Loop charPerType {
            password .= SubStr(chars, Random(1, StrLen(chars)), 1)
        }
    }
    passwords.Push(ShuffleString(password))
}

text := ""
for password in passwords {
    text .= password . "`r`n"
}

Run "notepad.exe"
WinWait "Untitled - Notepad"
WinActivate
Sleep 100

A_Clipboard := text
Send "^v"
Send "^{Home}"

ShuffleString(str) {
    chars := StrSplit(str)
    Loop chars.Length - 1 {
        j := Random(A_Index, chars.Length)
        temp := chars[A_Index]
        chars[A_Index] := chars[j]
        chars[j] := temp
    }
    return JoinChars(chars)
}

JoinChars(chars) {
    result := ""
    for char in chars {
        result .= char
    }
    return result
}
}
;;; ===============================================
ShowPercentageCalculator(*) {
per_calc := Gui("+AlwaysOnTop +ToolWindow")
per_calc.BackColor := "Black"
per_calc.SetFont("s11 c0ff768", "Consolas")

; Function to create an Edit control with white text
AddWhiteEdit(gui, options, text := "") {
    pcalc := gui.Add("Edit", options, text)
    pcalc.Opt("+Background202020 cWhite")  ; Dark gray background, white text
    return pcalc
}

per_calc.Add("Text", "x10 y10 w200 h16 +0x200", "What is         % of")
Per1 := AddWhiteEdit(per_calc, "x70 y08 w65 h20 vPer1 Right")
Per2 := AddWhiteEdit(per_calc, "x180 y08 w55 h20 vPer2 Right")
PerA := per_calc.Add("Text", "x240 y10 w70 h16 +0x200 vPerA")

Per3 := AddWhiteEdit(per_calc, "x10 y38 w65 h20 vPer3 Right")
per_calc.Add("Text", "x80 y40 w200 h16 +0x200", "is what % of ")
Per4 := AddWhiteEdit(per_calc, "x180 y38 w55 h20 vPer4 Right")
PerB := per_calc.Add("Text", "x240 y40 w70 h16 +0x200 vPerB")

Per5 := AddWhiteEdit(per_calc, "x10 y68 w65 h20 vPer5 Right")
per_calc.Add("Text", "x80 y72 w200 h16 +0x200", "is        % of what")
Per6 := AddWhiteEdit(per_calc, "x100 y68 w55 h20 vPer6 Right")
PerC := per_calc.Add("Text", "x240 y72 w70 h16 +0x200 vPerC")

per_calc.Add("Text", "x10 y100 w300 h16 +0x200", "-------- Find % of Gain/Loss --------")

per_calc.Add("Text", "x10 y128 w200 h16 +0x200", "From:          TO:")
Per7 := AddWhiteEdit(per_calc, "x55 y125 w70 h20 vPer7 Right")
Per8 := AddWhiteEdit(per_calc, "x160 y125 w75 h20 vPer8 Right")
PerD := per_calc.Add("Text", "x240 y128 w70 h16 +0x200 vPerD")

per_calc.OnEvent("Close", (*) => per_calc.Destroy())
per_calc.Title := "Percentage_Finder"
per_calc.Show("w350 h160")

; Event handlers
Per1.OnEvent("Change", CalcLabel0)
Per2.OnEvent("Change", CalcLabel0)
Per3.OnEvent("Change", CalcLabel1)
Per4.OnEvent("Change", CalcLabel1)
Per5.OnEvent("Change", CalcLabel2)
Per6.OnEvent("Change", CalcLabel2)
Per7.OnEvent("Change", CalcLabel3)
Per8.OnEvent("Change", CalcLabel3)

CalcLabel0(*) {
    PerA.Value := (Per1.Value != "" && Per2.Value != "") 
    ? Round((Per1.Value * Per2.Value) / 100, 2) 
    : ""
}

CalcLabel1(*) {
    PerB.Value := (Per3.Value != "" && Per4.Value != "") 
    ? Round((Per3.Value * 100) / Per4.Value, 2) . "%" 
    : ""
}

CalcLabel2(*) {
    PerC.Value := (Per5.Value != "" && Per6.Value != "") 
    ? Round((Per5.Value * 100) / Per6.Value) 
    : ""
}

CalcLabel3(*) {
    PerD.Value := (Per7.Value != "" && Per8.Value != "") 
    ? Round(((Per8.Value - Per7.Value) / Per7.Value) * 100, 2) . "%" 
    : ""
}
}
;;; ===============================================
checkurl_in_virustotal(){
copy2clip()
; MsgBox copy2clip()
if BrowserTabFinder("VirusTotal - Home") {
    WinWaitActive "VirusTotal - Home"    
    sendw('^v', 2000)
    sendw('{Enter}')
} else {
    Run "https://www.virustotal.com/gui/home/url"
    WinWaitActive "VirusTotal - Home"    
    sendw('^v', 2000)
    sendw('{Enter}')
}
}
; ===>> odified version to work with any default browser on any PC:
BrowserTabFinder(title) {
; Set the title matching mode to 'contains'
SetTitleMatchMode 2

; Define an array of common browser executable names
browsers := ["chrome.exe", "firefox.exe", "msedge.exe", "opera.exe", "brave.exe", "iexplore.exe", "safari.exe"]

; Loop through each browser in the array
for _, browser in browsers {
    ; Check if the current browser is running
    if WinExist("ahk_exe " . browser) {
        ; Activate the browser window
        WinActivate
        ; Get the title of the current tab
        originalTitle := WinGetTitle("A")
        ; Initialize tab counter
        tabCount := 0
        
        ; Start looping through tabs
        Loop {
            ; Increment tab counter
            tabCount++
            ; Switch to the next tab
            Send "^{Tab}"
            ; Wait a bit for the tab to load
            Sleep 100
            
            ; Check if we're still in the browser window
            if WinActive("ahk_exe " . browser) {
                ; Get the title of the current tab
                currentTitle := WinGetTitle("A")
                ; Check if the current tab title contains our target
                if InStr(currentTitle, title) {
                    ; If found, activate the window and return true
                    WinActivate
                    return true
                }
                ; If we've looped back to the start or checked 50 tabs, stop searching
                if (currentTitle == originalTitle || tabCount > 50) {
                    break
                }
            } else {
                ; If we've lost focus on the browser window, show a message and return false
                ToolTip "Browser window lost focus. Total tabs counted: " . tabCount
                SetTimer () => ToolTip(), -5000
                return false
            }
        }
    }
}

; If no supported browser is found or target tab not found, show a message and return false
ToolTip "No supported browser found or target tab not found"
SetTimer () => ToolTip(), -5000
return false
}
BrowserTabUrlFinder(url) {
SetTitleMatchMode 2

browsers := ["chrome.exe", "firefox.exe", "msedge.exe", "opera.exe", "brave.exe", "iexplore.exe", "safari.exe"]

for _, browser in browsers {
    if WinExist("ahk_exe " . browser) {
        WinActivate
        originalTitle := WinGetTitle("A")
        tabCount := 0
        
        Loop {
            tabCount++
            Send "^{Tab}"
            Sleep 300
            
            if WinActive("ahk_exe " . browser) {
                currentTitle := WinGetTitle("A")
                
                ; Get the URL of the current tab
                Send "^l"
                Sleep 500
                currentUrl := A_Clipboard
                A_Clipboard := ""  ; Clear clipboard
                Send "^c"
                ClipWait 1
                if (A_Clipboard != "") {
                    currentUrl := A_Clipboard
                }
                Send "{Esc}"  ; Deselect the URL
                
                ; Check if the current URL matches using InStr
                if InStr(currentUrl, url) {
                    WinActivate
                    return true
                }
                
                ; Check if the current URL matches using RegExMatch
                if RegExMatch(currentUrl, url) {
                    WinActivate
                    return true
                }
                
                if (currentTitle == originalTitle || tabCount > 50) {
                    break
                }
            } else {
                ToolTip "Browser window lost focus. Total tabs counted: " . tabCount
                SetTimer () => ToolTip(), -5000
                return false
            }
        }
    }
}

ToolTip "No supported browser found or target URL not found"
SetTimer () => ToolTip(), -5000
return false
}
SendWhatsAppMessage(phoneNumber, message) {
; Replace spaces with '%20' in the message
encodedMessage := StrReplace(StrReplace(message, " ", "%20"), "`n", "%0A")

; Construct the WhatsApp Web URL
wtsapp := 'https://web.whatsapp.com/send?phone=+91' . phoneNumber . '&text=' . encodedMessage

appsName := "chrome.exe"
if ProcessExist(appsName) {
WinActivate "ahk_exe " . appsName
Run 'chrome.exe ' . wtsapp
WinWaitActive 'WhatsApp'
Sleep 10000
SendEvent "{Blind}{Enter}"
} else {
; Open the URL in Chrome
Run 'chrome.exe ' . wtsapp
WinWaitActive 'WhatsApp'
Sleep 10000
SendEvent "{Blind}{Enter}"
}
}
; Create the GUI
MyWa := Gui()
MyWa.Title := "WhatsApp Message Sender"

; Add input boxes and labels
MyWa.Add("Text", "x10 y10 w120", "WhatsApp Number:")
MyWa.Add("Edit", "x10 y30 w200 vPhoneNumber")

MyWa.Add("Text", "x10 y60 w120", "Message:")
MyWa.Add("Edit", "x10 y80 w200 h60 vMessage")

; Add a submit button
submitBtn := MyWa.Add("Button", "x10 y150 w100", "Send")
submitBtn.OnEvent("Click", SendMessage)

; Show the GUI
wa_send(){
MyWa.Show()
}
; Function to handle the submit button click
SendMessage(*) {
enteredPhoneNumber := MyWa['PhoneNumber'].Value
enteredMessage := MyWa['Message'].Value

; Call the function to send WhatsApp message
SendWhatsAppMessage(enteredPhoneNumber, enteredMessage)
}
CopyFileContent() {
A_Clipboard := ""  ; Clear the clipboard
Send "^c"
ClipWait 2
if (A_Clipboard != "") {
    if (FileExist(A_Clipboard)) {
        try {
            fileContent := FileRead(A_Clipboard)
            ; MsgBox fileContent
            A_Clipboard := fileContent
            ToolTip("File content copied to clipboard successfully.")
            SetTimer () => ToolTip(), -5000  ; Hides the tooltip after 5 seconds
        } catch as err {
            MsgBox "Error reading file: " . err.Message
        }
    } else {
        MsgBox "Clipboard content is not a valid file path."
    }
} else {
    MsgBox "No content was copied to the clipboard."
}
}
;;================= ˅˅˅˅ news functions ˅˅˅˅ ==============
general_news(){
copy2clip()
Run "https://news.google.com/search?q=" . A_Clipboard
Run "https://www.bbc.com/search?q=" . A_Clipboard
Run "https://edition.cnn.com/search?q=" . A_Clipboard
Run "https://www.nytimes.com/search?query=" . A_Clipboard
Run "https://www.reuters.com/site-search/?query=" . A_Clipboard
Run "https://timesofindia.indiatimes.com/topic/" . A_Clipboard
Run "https://www.hindustantimes.com/topic/" . A_Clipboard
Run "https://www.ndtv.com/search?searchtext=" . A_Clipboard
}
Technology_News(){
copy2clip()
Run "https://news.google.com/search?q=" . A_Clipboard
Run "https://techcrunch.com/?s=" . A_Clipboard
Run "https://www.wired.com/search/?q=" . A_Clipboard
Run "https://www.theverge.com/search?q=" . A_Clipboard
Run "https://www.gadgets360.com/search?searchtext=" . A_Clipboard
Run "https://www.firstpost.com/tag/" . A_Clipboard
}
Financial_News(){
    copy2clip()
    Run "https://news.google.com/search?q=" . A_Clipboard
    Run "https://www.bloomberg.com/search?query=" . A_Clipboard
    Run "https://www.wsj.com/search?query=" . A_Clipboard
    Run "https://www.ft.com/search?q=" . A_Clipboard
    Run "https://www.google.com/search?q=" . A_Clipboard . " site:https://economictimes.indiatimes.com/"
    Run "https://www.google.com/search?q=" . A_Clipboard . " site:www.moneycontrol.com"
}
Science_News(){
    copy2clip()
    Run "https://news.google.com/search?q=" . A_Clipboard
    Run "https://www.sciencedaily.com/search/?keyword=" . A_Clipboard
    Run "https://www.nature.com/search?q=" . A_Clipboard
    Run "https://www.sciencenews.org/?s=" . A_Clipboard
    Run "https://www.thehindu.com/search/#gsc.tab=0&gsc.q=" . A_Clipboard    
}
World_News(){
    copy2clip()
    Run "https://www.aljazeera.com/search/" . A_Clipboard
    Run "https://www.google.com/search?q=" . A_Clipboard . " site:www.theguardian.com"
    Run "https://www.bbc.co.uk/search?q=" . A_Clipboard . '&edgeauth=eyJhbGciOiAiSFMyNTYiLCAidHlwIjogIkpXVCJ9.eyJrZXkiOiAiZmFzdGx5LXVyaS10b2tlbi0xIiwiZXhwIjogMTcyMTIxMjIzNSwibmJmIjogMTcyMTIxMTg3NSwicmVxdWVzdHVyaSI6ICIlMkZzZWFyY2glM0ZxJTNEbW9kaSJ9.KNiu7MlaE4X2pSi7oH22yYzS-4aBqn1MjZDiJGoONkY'
    Run "https://www.indiatoday.in/search/" . A_Clipboard
    Run "https://www.google.co.in/search?q=" . A_Clipboard . " site:https://indianexpress.com"    
}
Social_Media_News(){
    copy2clip()
    Run "https://www.facebook.com/search/top/?q=" . A_Clipboard
    Run "https://x.com/search?q=" . A_Clipboard . "&src=typed_query&f=top"
    Run "https://www.reddit.com/search/?q=" . A_Clipboard
    Run "https://news.google.com/search?q=" . A_Clipboard . "&hl=en-IN&gl=IN&ceid=IN%3Aen"
    Run "https://www.youtube.com/results?search_query=" . A_Clipboard .  "_News" . "&sp=EgIIAg%253D%253D"
; Run "https://www.linkedin.com/search/results/all/?keywords=" . A_Clipboard
}
;;================= ^^^^ news search functions ^^^^ ==============


;;================= ˅˅˅˅ social media search functions ˅˅˅˅ ==============

Social_Media(){
    copy2clip()
    Run "https://www.facebook.com/search/top/?q=" . A_Clipboard
; Run "https://www.linkedin.com/search/results/all/?keywords=" . A_Clipboard
    Run "https://x.com/search?q=" . A_Clipboard . "&src=typed_query&f=top"
    Run "https://www.reddit.com/search/?q=" . A_Clipboard
    Run "https://www.youtube.com/results?search_query=" . A_Clipboard
}
;;================= ^^^^ social media search functions ^^^^ ==============


;;================= ˅˅˅˅ Online shopping search functions ˅˅˅˅ ==============
Electronics(){
    copy2clip()
    Run "https://www.flipkart.com/search?q=" . A_Clipboard
    Run "https://www.amazon.in/s?k=" . A_Clipboard
    Run "https://www.tatacliq.com/search/?searchCategory=all&text=" . A_Clipboard
}
Fashion(){
    copy2clip()
    Run 'https://www.myntra.com/' . A_Clipboard . '?rawQuery=' . A_Clipboard
    Run 'https://www.ajio.com/search/?text=' . A_Clipboard
    Run 'https://www.amazon.in/s?k=' . A_Clipboard
    Run 'https://www.flipkart.com/search?q=' . A_Clipboard
}
Home_furniture(){
    copy2clip()
    Run 'https://www.pepperfry.com/site_product/search?q=' . A_Clipboard
    Run 'https://www.amazon.in/s?k=' . A_Clipboard
    Run 'https://www.flipkart.com/search?q=' . A_Clipboard
}
Groceries(){
    copy2clip()
Run 'https://www.bigbasket.com/ps/?q=' . A_Clipboard
Run 'https://www.amazon.in/s?k=' . A_Clipboard
Run 'https://www.flipkart.com/search?q=' . A_Clipboard
}
Beauty_Wellness(){
    copy2clip()
Run 'https://www.amazon.in/s?k=' . A_Clipboard
Run 'https://www.flipkart.com/search?q=' . A_Clipboard    
}
Books(){
    copy2clip()
Run 'https://www.amazon.in/s?k=' . A_Clipboard
Run 'https://www.flipkart.com/search?q=' . A_Clipboard    
}
Sports_Fitness(){
    copy2clip()
Run 'https://www.amazon.in/s?k=' . A_Clipboard
Run 'https://www.flipkart.com/search?q=' . A_Clipboard    
}
Toys_Baby_Products(){
    copy2clip()
Run 'https://www.amazon.in/s?k=' . A_Clipboard
Run 'https://www.flipkart.com/search?q=' . A_Clipboard
}
;;================= ^^^^ Online shopping search functions ^^^^ ==============

; googlesearch action for > selected text/non selected text 
; run > url with clip or run url with out clip
Runurl(urlclip,url){
    ClipSaved := ClipboardAll ; Save the current clipboard content
    A_Clipboard:=""
    Send "^c" ; Copy selected text
    ClipWait(1,1) ; timeout in 3sec and Wait for 1 sec to clipboard update
    Run (A_Clipboard ? urlclip . A_Clipboard : url) ; run url with clip or run url with out clip ; Ternary operator method: IsSet(A) ? A : B
    ClipSaved := A_Clipboard
}

;;=================> apply Dark Mode function ==============
;; got the dark mode solution from https://www.reddit.com/user/DepthTrawler/
SetPreferredAppMode()
; Build the menu, then call FlushMenuThemes
FlushMenuThemes()

AppsUseLightTheme() {
        keyName := "HKCU\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize"
        valueName := "AppsUseLightTheme"
        return RegRead(keyName, valueName)
}

SetPreferredAppMode(option := ""){
        static options := Map()
        if !options.Count {
                options.CaseSense := false
                options.Set(
                        "Default", 0,
                        "AllowDark", 1,
                        "ForceDark", 2,
                        "ForceLight", 3,
                        "Max", 4
                )
                options.Default := !AppsUseLightTheme()
        }
        hModule := DllCall("kernel32.dll\GetModuleHandle", "str", "uxtheme.dll", "ptr")
        ; These are undocumented functions. They must be called via ordinal.
        SetPreferredAppMode := DllCall("kernel32.dll\GetProcAddress", "ptr", hModule, "ptr", 135, "ptr")
        DllCall(SetPreferredAppMode, "int", options.Get(option))
        DllCall("kernel32.dll\FreeLibrary", "ptr", hModule)
}       

FlushMenuThemes() {
    hModule := DllCall("kernel32.dll\GetModuleHandle", "str", "uxtheme.dll", "ptr")
    ; Undocumented functions must be called via ordinal.
    FlushMenuThemes := DllCall("kernel32.dll\GetProcAddress", "ptr", hModule, "ptr", 136, "ptr")
    DllCall(FlushMenuThemes)
    DllCall("kernel32.dll\FreeLibrary", "ptr", hModule)
}


```
</details>

<br>


## 💡Password Generater:
![image](My_AHK_Project_Snaps/Password_Generator.png "Password_Generator")

<details>
<summary>Click to expand/collapse the code</summary>

```AutoHotkey
toggle source code ## ------- SOURCE CODE HERE
```
</details>

<br>
