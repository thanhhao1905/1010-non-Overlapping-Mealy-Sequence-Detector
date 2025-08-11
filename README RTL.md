```verilog
module seq_detector_1010_non_ovl (input wire clk,rst_n,x,
                                  output wire z);
  reg [3:0] state, next_state;
  parameter A = 4'b0000;
  parameter B = 4'b0001;
  parameter C = 4'b0010;
  parameter D = 4'b0101;
  
  always @ (posedge clk or negedge rst_n) begin
    if(rst_n == 0)
      state <= A;
    else 
      state <= next_state;
  end
      
  always @ (state or x) begin
      case (state )
      A: if(x==0) next_state = A;
      else next_state = B;
      
      B: if(x==0) next_state = C;
      else next_state = B;
      
      C: if(x==0) next_state = A;
      else next_state = D;
      
      D: if(x==0) next_state = A;
      else next_state = B;
      
      default: next_state = A;
    endcase
  end

  assign z = ((state == D) && (x == 0)) ? 1:0 ;
endmodule
