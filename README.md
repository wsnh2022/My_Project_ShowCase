# My_Project_PNG 

[The-Ultimate-Markdown-Cheat-Sheet](https://github.com/lifeparticle/Markdown-Cheatsheet)

## 💡ONE GUI Tab-1:
![Description of the image](My_AHK_Project_Snaps/ONE_GUI.png "ONE_GUI.png")

## ONE GUI Templates Manager Tab-2 :
![Description of the image](My_AHK_Project_Snaps/ONE_GUI_Templates_Manager.png "ONE_GUI_Templates_Manager")


# AHK Volume Control and Window Management

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
/** @var {GuiExt} MyGui */
MyGui := Gui()
; MyGui.Opt("+AlwaysOnTop")
MyGui.Title := "OneGui"
MyGui.BackColor := bc
/* To set Rounded Corners for window. */
MyGui.SetWindowAttribute(33, 2)
MyGui.SetDarkTitle()
MyGui.SetDarkMenu()
MyGui.SetWindowColor(, MyGui.BackColor, MyGui.BackColor)
/* This example sets dark mode edit control.*/
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

## 💡Action Menu:
![Description of the image](My_AHK_Project_Snaps/Action_Menu.png "Action_Menu")

## 💡Password Generater:
![image](My_AHK_Project_Snaps/Password_Generator.png "Password_Generator")


[code sample You can use numbers for reference-style link definitions][1]

Or leave it empty and use the [link text itself].

[arbitrary case-insensitive reference text]: https://www.mozilla.org
[1]: http://slashdot.org
[link text itself]: http://www.reddit.com
