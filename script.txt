function start(){
	if(document.getElementById("NFC").value ===""||document.getElementById("NFC").value == 0){
		alert("can't leave empty");
		return;
	}
	document.getElementById("container2").style.display = "none";
	document.getElementById("table").style.display = "block";
	document.getElementById("but2").style.display = "block";
	document.getElementById("but4").style.display = "block";
	var n = document.getElementById('NFC').value;
	addhead(n);	
	
}

function addhead(num){
	let ele =  document.getElementById("table");
	/*if(ele.columns.length == 0){
		break;
	}else{var head = ele.createTHead();
		var cell = row.insertCell(i);  
    	cell.innerHTML = "<input class='text1' type='text'></input>";
    }*/
	var head = ele.createTHead();
    var row =head.insertRow(0);
    for(let i = 0;i<num;i++){
    	var cell = row.insertCell(i);  
    	cell.innerHTML = "<input class='text1' type='text'></input>";
    }
    var c = row.insertCell(num);
    c.innerHTML ='delete';
    }


function addrow(){
	var n = document.getElementById('NFC').value;
	let ele =  document.getElementById("table");
	var len = ele.rows.length;
    var row =ele.insertRow(len);
    for(let i = 0;i<n;i++){
    var cell = row.insertCell(i);
    cell.innerHTML = "<input class='text1' type='text'></input>";
}
    var c = row.insertCell(n);
    c.innerHTML = '<button class="button1" onclick="deleterow('+len+')"><i class="fa fa-minus" aria-hidden="true"></i></button>';
    

     }

function deleterow(len){
	var n = document.getElementById('NFC').value;
  document.getElementById("table").deleteRow(len);
var ele = document.getElementById('table');
  for(let i=len ; i<=ele.rows.length+1; i++){
    table.rows[i].cells[n].innerHTML = '<button class="button1" onclick="deleterow('+ len +')"><i class="fa fa-minus" aria-hidden="true"></button>';
  }
}
function download(tableID, filename = 'Attendance'){


    var name= prompt('Excel file name?');

    var downloadLink;
    var dataType = 'application/vnd.ms-excel';
    var tableSelect = document.getElementById(tableID);
    var tableHTML = tableSelect.outerHTML.replace(/ /g, '%20');
    
    // Specify file name
    filename = filename?name+'.xls':'excel_data.xls';
    
    // Create download link element
    downloadLink = document.createElement("a");
    
    document.body.appendChild(downloadLink);
    
    if(navigator.msSaveOrOpenBlob){
        var blob = new Blob(['\ufeff', tableHTML], {
            type: dataType
        });
        navigator.msSaveOrOpenBlob( blob, filename);
    }else{
        // Create a link to the file
        downloadLink.href = 'data:' + dataType + ', ' + tableHTML;
    
        // Setting the file name
        downloadLink.download = filename;
        
        //triggering the function
        downloadLink.click();
    }
}
/*function save(){
	let table1;
	let table2 = document.getElementById('table');
	var head = table2.createTHead();
	var row =head.insertRow(0);
	for(let i = 0;i<table1.columns.length;i++){  
	    var cell = row.insertCell(i);  
    	cell.innerHTML = table2.;		  		 
	}
	var c = row.insertCell(table1.columns.length);
	for(let i =0; i<=table1.rows.length;i++){
		for(let j = 0; j<table1.columns.length;j++){

		}
	}
	document.getElementById("container2").style.display = "none";
	document.getElementById("table").style.display = "block";
	document.getElementById("but2").style.display = "block";
	document.getElementById("but4").style.display = "block";
	var n = document.getElementById('NFC').value;
	addhead(n);	
}
/*function addvalue(){
	var ele = document.getElementsById('table');
	var len = ele.rows.length;
	for(let i=0 ; i<len; i++){
		for(let j = 0; j<n;j++){
    table.rows[i].cells[n].innerHTML = ;
  }
}
}*/

	
	//var cell1 = row.insertCell(0);
	//var cell2 = row.insertCell(1);
	//var cell3 = row.insertCell(2);


		//cell1.innerHTML = "<input type='text'></input>";
		//cell2.innerHTML = "<input type='text'></input>";
		//cell3.innerHTML = "<input type='text'></input>";
//	for(let i=0;i<n;i++){
//		let cell = c.insertCell(i);
//		cell.innerHTML = "hello";
//	}