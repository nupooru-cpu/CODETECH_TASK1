module test;

reg clk;
reg d;
wire q;

dff uut(
    .clk(clk),
    .d(d),
    .q(q)
);

always #5 clk = ~clk;

initial
begin
    $dumpfile("dump.vcd");
    $dumpvars(0,test);

    clk = 0;
    d = 0;

    #10 d = 1;
    #10 d = 0;
    #10 d = 1;

    #20 $finish;
end

endmodule