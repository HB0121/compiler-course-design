@.fmt_int = private unnamed_addr constant [4 x i8] c"%d\0A\00"
declare i32 @printf(i8*, ...)

define i32 @main() {
entry:
  %i = alloca i32
  %limit = alloca i32
  %total = alloca i32
  store i32 3, i32* %limit
  store i32 0, i32* %i
  store i32 0, i32* %total
  br label %L8
L8:
  %v1 = load i32, i32* %i
  %v2 = load i32, i32* %limit
  %cmp1 = icmp slt i32 %v1, %v2
  br i1 %cmp1, label %L10, label %L17
L10:
  %v3 = load i32, i32* %total
  %v4 = load i32, i32* %i
  %t2 = add i32 0, 0
  store i32 %t2, i32* %total
  %v5 = load i32, i32* %i
  %t3 = add i32 %v5, 1
  store i32 %t3, i32* %i
  br label %L8
L17:
  %v6 = load i32, i32* %total
  call i32 (i8*, ...) @printf(i8* getelementptr inbounds ([4 x i8], [4 x i8]* @.fmt_int, i32 0, i32 0), i32 %v6)
  %t4 = add i32 0, 0
  ret i32 0
}
