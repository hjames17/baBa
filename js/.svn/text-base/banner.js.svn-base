	$(document).ready(function(){
		
		var page = 1;
		
		var i = 1;
		
		//ÏòÓÒÒÆ¶¯
		
		$(".nextt").click(function(){
			
			var jq1 = $(this).parents(".a1");
			
			var jq2 = jq1.find(".a6");
			
			var jq3 = jq1.find(".a5");
			
			var jqwidth = jq3.width();
			
			var len = jq2.find("li").length;
			
			var page_count = Math.ceil(len/i);
			
			if(!jq2.is(":animated")){
				
				if (page == page_count){
					
				jq2.animate({left:'0px'},"slow");
				
				page = 1;					
	
					}else{
					
				jq2.animate({left:'-='+jqwidth},"slow");
				
				page++;	
						
				}				
				
			}
			
			
		});
		
		
		//Ïò×óÒÆ¶¯
		
		$(".prev").click(function(){
			
			var jq1 = $(this).parents(".a1");
			
			var jq2 = jq1.find(".a6");
			
			var jq3 = jq1.find(".a5");
			
			var jqwidth = jq3.width();
			
			var len = jq2.find("li").length;
			
			var page_count = Math.ceil(len/i);
			
			if(!jq2.is(":animated")){
				
				if (page == 1){
					
				jq2.animate({left:'-='+jqwidth*(page_count-1)},"slow");
				
				page = page_count;					
	
					}else{
					
				jq2.animate({left:'+='+jqwidth},"slow");
				
				page--;	
						
				}				
				
			}
			
		
		
		});
		
		







});