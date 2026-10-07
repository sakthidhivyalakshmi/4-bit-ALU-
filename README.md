 


# 4-bit Arithmetic Logic Unit (ALU)

module ALU (
    input  [3:0] A,
    input  [3:0] B,
    input  [2:0] ALU_Sel,
    output reg [3:0] Result,
    output reg       Carry,
    output           Zero
);

always @(*) begin
    Result = 4'b0000;
    Carry  = 1'b0;

    case (ALU_Sel)

        3'b000: begin
            {Carry, Result} = A + B;       // Addition
        end

        3'b001: begin
            {Carry, Result} = A - B;       // Subtraction
        end

        3'b010: begin
            Result = A & B;                // AND
        end

        3'b011: begin
            Result = A | B;                // OR
        end

        3'b100: begin
            Result = A ^ B;                // XOR
        end

        3'b101: begin
            Result = ~A;                   // NOT
        end

        3'b110: begin
            Result = A << 1;               // Left Shift
        end

        3'b111: begin
            Result = A >> 1;               // Right Shift
        end

        default: begin
            Result = 4'b0000;
            Carry  = 1'b0;
        end

    endcase
end

assign Zero = (Result == 4'b0000);

endmodule


#testbench
`timescale 1ns/1ps

module ALU_tb;

reg  [3:0] A;
reg  [3:0] B;
reg  [2:0] ALU_Sel;

wire [3:0] Result;
wire       Carry;
wire       Zero;

ALU uut (
    .A(A),
    .B(B),
    .ALU_Sel(ALU_Sel),
    .Result(Result),
    .Carry(Carry),
    .Zero(Zero)
);

initial begin

    // Addition
    A = 4'b0101;
    B = 4'b0011;
    ALU_Sel = 3'b000;
    #10;

    // Subtraction
    A = 4'b1000;
    B = 4'b0011;
    ALU_Sel = 3'b001;
    #10;

    // AND
    A = 4'b1100;
    B = 4'b1010;
    ALU_Sel = 3'b010;
    #10;

    // OR
    A = 4'b1100;
    B = 4'b1010;
    ALU_Sel = 3'b011;
    #10;

    // XOR
    A = 4'b1100;
    B = 4'b1010;
    ALU_Sel = 3'b100;
    #10;

    // NOT
    A = 4'b1010;
    B = 4'b0000;
    ALU_Sel = 3'b101;
    #10;

    // Left Shift
    A = 4'b0011;
    B = 4'b0000;
    ALU_Sel = 3'b110;
    #10;

    // Right Shift
    A = 4'b1100;
    B = 4'b0000;
    ALU_Sel = 3'b111;
    #10;

    $finish;
end

endmodule

