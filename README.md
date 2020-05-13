# 0903test
<!DOCTYPE html>
<html>
<head>
<script type="text/javascript">
function fillHidTable(){
    var htqf; //-- hidden field
    var rf; //-- retrieved field
    for ( var i = 1; i < 5; i++ ) {
        rf = "htqf"+i;
        document.getElementById(rf).innerHTML = document.getElementById("Q"+i+"CALC").value;
    }
    tableToExcel('hidTable', 'Analysis Results');
}

var tableToExcel = (function() {
    var uri = 'data:application/vnd.ms-excel;base64,'
            , template = '<html xmlns:o="urn:schemas-microsoft-com:office:office" xmlns:x="urn:schemas-microsoft-com:office:excel" xmlns="http://www.w3.org/TR/REC-html40"><head><!--[if gte mso 9]><xml><x:ExcelWorkbook><x:ExcelWorksheets><x:ExcelWorksheet><x:Name>{worksheet}</x:Name><x:WorksheetOptions><x:DisplayGridlines/></x:WorksheetOptions></x:ExcelWorksheet></x:ExcelWorksheets></x:ExcelWorkbook></xml><![endif]--></head><body><table>{table}</table></body></html>'
            , base64 = function(s) { return window.btoa(unescape(encodeURIComponent(s))) }
            , format = function(s, c) { return s.replace(/{(\w+)}/g, function(m, p) { return c[p]; }) }
    return function(table, name) {
        if (!table.nodeType) table = document.getElementById(table)
        var ctx = {worksheet: name || 'Worksheet', table: table.innerHTML}
        window.location.href = uri + base64(format(template, ctx))
    }
})()
</script>

<title>HTML Form Data to Excel</title>

<style type="text/css" media="screen">
    .divCenMid{font-family:Arial,sans-serif;font-size:14pt;font-style:normal;font-weight:700;text-align:center;vertical-align:middle;margin:0;}
    .allbdrCenMid{border:.75pt solid windowtext;color:#000;font-family:Arial,sans-serif;font-size:10pt;font-style:normal;font-weight:400;text-align:center;vertical-align:middle;margin:0;}
    .allbdrCenTop{border:.75pt solid windowtext;color:#000;font-family:Arial,sans-serif;font-size:10pt;font-style:normal;font-weight:400;text-align:center;vertical-align:top;margin:0;}
    .allbdrLtMid{border:.75pt solid windowtext;color:#000;font-family:Arial,sans-serif;font-size:10pt;font-style:normal;font-weight:400;text-align:left;vertical-align:middle;margin:0;}
    .allbdrLtTop{border:.75pt solid windowtext;color:#000;font-family:Arial,sans-serif;font-size:10pt;font-style:normal;font-weight:400;text-align:left;vertical-align:top;margin:0;}

</style>

</head>

<body>

<table width= "565px" cellspacing="0" cellpadding="0" style="border-spacing:0;" id="QMSTable">
    <col width="25px"/>
    <col width="120px"/>
    <col width="360px"/>
    <col width="60px"/>
    <tr>
        <td class="divCenMid" colspan = "4"> QMS Assessment</td>
    </tr>
    <tr>
        <td class="allbdrCenMid"> No</td>
        <td class="allbdrCenMid"> Criteria</td>
        <td class="allbdrLtMid"> Question</td>
        <td class="allbdrCenMid"> Score</td>
    </tr>
    <tr>
        <td class="allbdrCenTop"> Q1</td>
        <td class="allbdrLtTop"> Quality Unit Independency</td>
        <td class="allbdrLtTop"> Do you have the Quality Unit?</td>
        <td class="allbdrCenMid">
            <input id="Q1CALC" type="text" value="" class="nobdrCenMid" style="overflow:hidden; width:93% " name="Q1CALC"/>
        </td>
    </tr>
    <tr>
        <td class="allbdrCenTop"> Q2</td>
        <td class="allbdrLtTop"> Apply PICS GMP</td>
        <td class="allbdrLtTop"> Which GMP regulation do you use?</td>
        <td class="allbdrCenMid">
            <input id="Q2CALC" type="text" value="" class="nobdrCenMid" style="overflow:hidden; width:93% " name="Q2CALC"/>
        </td>
    </tr>
    <tr>
        <td class="allbdrCenTop"> Q3</td>
        <td class="allbdrLtTop"> Deviation or Non-conformance</td>
        <td class="allbdrLtTop"> Do you have a deviation or non-conformance procedure?</td>
        <td class="allbdrCenMid">
            <input id="Q3CALC" type="text" value="" class="nobdrCenMid" style="overflow:hidden; width:93% " name="Q3CALC"/>
        </td>
    </tr>
    <tr>
        <td class="allbdrCenTop"> Q4</td>
        <td class="allbdrLtTop"> Complaint</td>
        <td class="allbdrLtTop"> Do you have a customer complaint procedure?</td>
        <td class="allbdrCenMid">
            <input id="Q4CALC" type="text" value="" class="nobdrCenMid" style="overflow:hidden; width:93% " name="Q4CALC"/>
        </td>
    </tr>
</table>

<div id="hidTable" style="display: none">
    <table id="testTable">
        <caption>Supplier Risk Analysis</caption>
        <colgroup></colgroup>
        <colgroup></colgroup>
        <colgroup></colgroup>
        <thead>
        <tr>
            <th>No.</th>
            <th>Question</th>
            <th>Score</th>
        </tr>
        </thead>
        <tbody>
        <tr>
            <td>Q1</td>
            <td>Do you have the Quality Unit?</td>
            <td id="htqf1">-</td>
        </tr>
        <tr>
            <td>Q2</td>
            <td>Apply PICS GMP?</td>
            <td id="htqf2">-</td>
        </tr>
        <tr>
            <td>Q3</td>
            <td>Do you have a deviation or non-conformance procedure?</td>
            <td id="htqf3">-</td>
        </tr>
        <tr>
            <td>Q4</td>
            <td>Do you have a customer complaint procedure?</td>
            <td id="htqf4">-</td>
        </tr>
        </tbody>
    </table>
</div>

<input type="button" onclick="fillHidTable()" value="Export Data to Excel">
</body>
</html>

