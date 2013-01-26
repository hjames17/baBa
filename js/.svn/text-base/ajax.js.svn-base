
	var base = 'http://42.120.63.120/';
	var start = 0;
	var firstLoad = 0;
	var end=false;
    var size=0;
			// var content =	"<li><div class='img_box' id='matter_1'><a href='"+item.click_url+"' class='super_a'>"+ 
			// 				"<img src='"+item.pic_url+"' width='220' height='242' /></a></div>"+
			// 	              "<h1><a href='"+item.click_url+"'>"+item.title+"</a>  "+'销量：'+ "  "+item.volume+"   </h1>"+
			// 	             "<p class='xiaoliang' >  </p>"+
			// 	              "<h3> <a href='"+item.shop_click_url+"' class='kankan'> 去店铺看看</a>"+
			// 	               "<div class='bt'> <span><a href='"+item.click_url+"' class='Price'>价格："+item.price+"</a> </span> <span><a href='"+item.click_url+"' class='gogo_1'>去购买</a></span></div>"+
			// 	              "</h3></li>";
    var liCreation = function(data) {
    		$.each(data,function(i,item){
				//// div part
				//<img src='"+item.pic_url+"' width='220' height='242' />
				var img = $("<img/>");
				img.attr("src", item.pic_url)
				   .attr("width", "220")
				   .attr("height", "242");
				//<a href='"+item.click_url+"' class='super_a'>img</a>   
				var a = $("<a/>");
				a.attr("href", item.click_url).attr("class", "super_a").append(img);
				//div
				var div = $("<div/>");
				div.attr("class","img_box").attr("id","matter_1").append(a);
				
				////h1 part
				var a10 = $("<a/>");
				a10.attr("href", item.click_url).append(item.title);

				var h1 = $("<h1/>");
				h1.text("销量："+item.volume).append(a10);

				//// p part
				var p = $("<p/>");
				p.attr("class","xiaoliang");

				////h3 part
				var a2 = $("<a/>");
				a2.attr("href", item.shop_click_url).attr("class", "kankan").text("去店铺看看");
				var div1 = $("<div/>");
				div1.attr("class","bt");
				var a3 = $("<a/>");
				a3.attr("href", item.click_url).attr("class", "Price").text("价格："+item.price);
				var a4 = $("<a/>");
				a4.attr("href", item.click_url).attr("class", "gogo_1").text("去购买");
				//note: 是a,不是a4
				a.hover(function(){
							//alert(a4.toString());
							$(this).addClass("hovers").siblings();
							a4.animate({top:"-30px"},"slow");
						},function(){ 
							//alert("2");
							$(this).removeClass("hovers").siblings();
							a4.animate({top:"0px"},"slow");		
				});
				var span1 = $("<span/>");
				span1.append(a3);
				var span2 = $("<span/>");
				span2.append(a4);
				div1.append(span1).append(span2);
				var h3 = $("<h3/>");
				h3.append(a2).append(div1);

				////li part
				var liElement = $("<li/>");
				liElement.append(div).append(h1).append(p).append(h3);
					
				$("#content").append(liElement);
				})
			
			};


    function showBoy(){
    	var ho = $(".Total_category");
    	ho.hover(function(){
    		$(this).children(".Total_children").show();
    	 	$(this).children("a").addClass('hovers');
    	},function(){
    		$(".Total_category").children(".Total_children").hide();
    		$(this).children("a").removeClass('hovers');
    	});
    };

	$(function(){	
			//对content使用masonry插件
			$(".next_page a").click(function(){
				//首先取得下一页的链接地址s
				start = $("#content").find("li").length;
				var href=$(this).attr("href");
				$(".next_page a").attr('href',href);
				//判断下一页的链接地址是否存在
				if( href != undefined ){
					//如果存在的话，用ajax获取数据
					$.getJSON(href+ start+"&size="+size, function(data) {
						var content="";
						if(data.success!=null){
							end=true;
							alert("没有内容了");
						}else{
							liCreation(data);
							
							//$("#content").append( content );
						}
					});
				}
				
				//返回false，使得点击进入新页面失效
				return false;
			})
			
				//首先给窗口绑定事件scroll
		$(window).bind("scroll",function(){
		// 然后判断窗口的滚动条是否接近页面底部，这里的30可以自定义
		if( $(document).scrollTop() + $(window).height() > $(document).height() - 30 ){
		 if(!end){
			$(".next_page a").trigger("click");
		 }
		}
		})





	});
	function loadInfo(url) {
		var get = base + url;
		size=getSize();
		$.getJSON(get, function(data) {
			loadItem(data[0].url);
			$("#menu").html("");
			$.each(data, function(i, item) {
				var content=
					"<div class='Total_category'>" +"<a class='carte' onclick=loadItem('"+ item.url + "')>" + item.name 
					 +"</a>"+"<ul class='Total_children'>"+"<div class='bao_li'>";
				$.each(item.children, function(j, item) {
					content=content+
					"<li class='sort'>"+ 
					"<a href='#' onclick=loadItem('"+ item.url + "')>" + item.name + "("+ item.count + ")" + "</a></li>";
				});
				$("#menu").append(content);
			});
			showBoy();
		});
	
	};
	function loadItem(url) {  
		start = 0;
		if (firstLoad == 0) {
			firstLoad = 1
		} else {
			$("#content").html("");
		}
		$(".next_page a").attr('href',""); 
		$(".next_page a").attr('href',url+"&callback=?&no=");
		$.getJSON(url + "&callback=?&no=" + start+"&size="+size, function(data) {
				//$.each(data, liCreation(i,item));
				liCreation(data);
				start = $("#content").find("li").length;
			});		
		end=false;
	};
	function getSize(){
		var winWidth = $(window).width();
		if(	winWidth>980 ){	
	     	var main=980;
		}else if(winWidth<980){	
		    var main=480;		
		}else if(winWidth<980 &&  winWidth>480){	
		    var main=480;		
		}
		var liWidth = 220;
		var marginRight =30;
		var size = parseInt(main+marginRight)/(liWidth+marginRight); //计算出size
		return size;
	}

function log(message) {  
    if (!log.window_ || log.window_.closed) {  
        var win = window.open("", null, "width=400,height=200," +  
                              "scrollbars=yes,resizable=yes,status=no," +  
                              "location=no,menubar=no,toolbar=no");  
        if (!win) return;  
        var doc = win.document;  
        doc.write("<html><head><title>Debug Log</title></head>" +  
                  "<body></body><html>");  
        doc.close();  
        log.window_ = win;  
    }  
    var logLine = log.window_.document.createElement("div");  
    logLine.appendChild(log.window_.document.createTextNode(message));  
    log.window_.document.body.appendChild(logLine);  
}  









