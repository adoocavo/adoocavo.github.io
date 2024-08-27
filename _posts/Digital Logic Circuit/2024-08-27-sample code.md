---
title:  "Sample code"
typora-root-url: ../../

---

## [Verilog Sample Code]

### #1. JK FF 

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



### #2. JK FF TestBench

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

[코드 출처]: https://verificationguide.com/verilog-examples/

