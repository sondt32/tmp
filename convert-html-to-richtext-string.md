# Hàm convert html thành chuỗi richtext hiển thị đẹp trên unity tương thích nhiều thẻ html
```
using System.Text.RegularExpressions;

string ConvertHtml(string html)
{
    string result = html;

    // ===== HEADINGS =====
    result = Regex.Replace(result, @"<h1>(.*?)</h1>", "<size=32><b>$1</b></size>\n");
    result = Regex.Replace(result, @"<h2>(.*?)</h2>", "<size=28><b>$1</b></size>\n");
    result = Regex.Replace(result, @"<h3>(.*?)</h3>", "<size=24><b>$1</b></size>\n");

    // ===== BOLD / ITALIC / UNDERLINE =====
    result = result.Replace("<b>", "<b>").Replace("</b>", "</b>");
    result = result.Replace("<strong>", "<b>").Replace("</strong>", "</b>");
    result = result.Replace("<i>", "<i>").Replace("</i>", "</i>");
    result = result.Replace("<em>", "<i>").Replace("</em>", "</i>");
    result = result.Replace("<u>", "<u>").Replace("</u>", "</u>");

    // ===== PARAGRAPH =====
    result = result.Replace("<p>", "").Replace("</p>", "\n");

    // ===== LINE BREAK =====
    result = result.Replace("<br>", "\n").Replace("<br/>", "\n").Replace("<br />", "\n");

    // ===== LIST =====
    result = result.Replace("<ul>", "").Replace("</ul>", "");
    result = result.Replace("<ol>", "").Replace("</ol>", "");

    // li → bullet
    result = Regex.Replace(result, @"<li>(.*?)</li>", "• $1\n");

    // ===== COLOR =====
    result = Regex.Replace(result, 
        @"<span style=""color:(.*?)"">(.*?)</span>", 
        "<color=$1>$2</color>");

    // ===== REMOVE OTHER TAGS =====
    result = Regex.Replace(result, "<.*?>", "");

    // ===== CLEAN =====
    result = result.Replace("&nbsp;", " ");
    result = result.Replace("&lt;", "<");
    result = result.Replace("&gt;", ">");
    result = result.Replace("&amp;", "&");

    return result.Trim();
}
```
