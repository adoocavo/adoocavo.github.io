---
title:  "Sample code"
typora-root-url: ../../
categories: Digital&nbspLogic&nbspCircuit
tag: [디지털공학, verilog]
layout: single
toc: true 		#포스트 내에서 내용 관련 목차 보이기
author_profile: false  #포스트 내에서 왼쪽 profile 보이기
sidebar:
    nav: "docs" #포스트 내에서 왼쪽에 docs 보이기
---

notice 기능 test
{: .notice--warning}

<div class="notice--warning">
  <h4>notice 기능 test</h4>  
  <ul>
		<li>1. 이렇게 된다</li>	  
		<li>2. 이렇게 된다</li>
  	<li>3. 우왕</li>    
  </ul>
</div>
[버튼 기능 test(커리큘럼)](https://www.inflearn.com/course/반도체-아날로그-회로설계-실무-digital-ip){: .btn}

## 1. JK-FF

```verilog
// JK-FF
module jdflipflop(q,qbar,clk,rst,d);
	output reg q;
	output qbar;
	input clk, rst;
	input d;

	assign qbar = ~q;

	always @(posedge clk)
	begin
		if (rst)
			q <= 0;
		else
			q <= d;
	end
endmodule
```

### 설명1

- JK FF는 ~~

### 설명2

- JK FF는 ~~



## 2. JK-FF TestBench

```verilog
// JK-FF TestBench 
module jdflipfloptb;
	wire q, qbar;
	reg clk,rst;
	reg d;

	jdflipflop jdff(q,qbar,clk,rst,d);
	always #5 clk = ~clk;

	initial
	begin
                clk = 1'b0;
		rst = 1; # 10; rst = 0; #10; 
		$display("RSLT\td\tq\tqbar");
                d = 0; # 10; // Another value
                if ( q === 1'b0 ) // Test for inversion
                        $display ("PASS\t%d\t%d\t%d",d,q,qbar);
                else
                        $display ("FAIL\t%d\t%d\t%d",d,q,qbar);
		
                d = 1; # 10; // Another value
                if ( q === 1'b1 ) // Test for inversion
                        $display ("PASS\t%d\t%d\t%d",d,q,qbar);
                else
                        $display ("FAIL\t%d\t%d\t%d",d,q,qbar);

		#10;
		$finish;		
	end
  
  //enabling the wave dump
  initial begin 
    $dumpfile("dump.vcd"); $dumpvars;
  end
endmodule
```

### 설명1

- JK FF는 ~~

### 설명2

- JK FF는 ~~

[코드 출처]: https://verificationguide.com/verilog-examples/

