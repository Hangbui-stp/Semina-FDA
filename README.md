1. Mục tiêu bài toán: Dự đoán tình trạng khó khăn tài chính và phá sản của doanh nghiệp bằng mô hình truyền thống và GNN, kết hợp Causual graph		
2. Dataset:	Bao gồm 45 chỉ số và tỷ lệ tài chính của tất cả các công ty thuộc chỉ số Nasdaq-100 trong trong giai đoạn từ năm 2017 đến 2022, nguồn Kaggle: https://www.kaggle.com/datasets/ifuurh/nasdaq100-fundamental-data                     		
	Bộ dữ liệu còn có một trường Latest Data, tuy nhiên giai đoạn này dữ liệu rất hạn chế. Tổng cộng, bộ dữ liệu bao gồm 7 kỳ dữ liệu theo năm.		
			
3. Các vấn đề của dataset gốc:
    Có nhiều thuộc tính dữ liệu không đầy đủ tất cả các năm.	 
	→  loại bỏ các thuộc tính không được điền dữ liệu đầy đủ qua các kỳ năm.	 
	Có nhiều giá trị bị thiếu (NaN) hoặc vô hạn (Inf).		 
	→ điền các giá trị thiếu bằng những giá trị hợp lý và có ý nghĩa tài chính.		 
	Dữ liệu dạng wide-format cross-section với biến thời gian mở rộng (time-expanded wide data)		 
	→ đưa về dạng Panel 		 
	Dataset chưa có nhãn (label) cho bài toán ML.		 
			
5. Các chỉ số và tỷ lệ:       
    1	Vòng quay tài sản - Asset Turnover      
	2	Lợi suất mua lại cổ phiếu - Buyback Yield                    
	3	CAPEX trên doanh thu - CAPEX to Revenue                  
	4	Tỷ lệ tiền mặt - Cash Ratio                    
	5	Tiền mặt trên nợ - Cash to Debt       
	6	Giá vốn hàng bán trên doanh thu - COGS to Revenue       
	7	Chỉ số Beneish M-Score - Beneish M-Score       
	8	Chỉ số Altman Z-Score - Altman Z-Score (Nhãn nhị phân_zscore dùng để đo chỉ số rủi ro phá sản, theo cắt điểm tối ưu được Altman rút ra từ dữ liệu thực nghiệm nếu <1.8 là nguy cơ phá sản cao (1) hoặc ngược lại nguy cơ thấp (0) )    
	9	Tỷ lệ thanh toán hiện hành - Current Ratio       
	10	Số ngày tồn kho - Days Inventory       
	11	Nợ trên vốn chủ sở hữu - Debt to Equity       
	12	Nợ trên tổng tài sản - Debt to Assets       
	13	Nợ trên EBITDA - Debt to EBITDA       
	14	Nợ trên doanh thu - Debt to Revenue       
	15	E10 (theo GS. Robert Shiller) - E10       
	16	Lãi suất hiệu dụng - Effective Interest Rate       
	17	Vốn chủ sở hữu trên tổng tài sản - Equity to Assets       
	18	Giá trị doanh nghiệp trên EBIT - Enterprise Value to EBIT       
	19	Giá trị doanh nghiệp trên EBITDA - Enterprise Value to EBITDA       
	20	Giá trị doanh nghiệp trên doanh thu - Enterprise Value to Revenue       
	21	Khó khăn tài chính - Financial Distress       
	22	Sức mạnh tài chính - Financial Strength       
	23	Earnings Yield theo Joel Greenblatt - Earnings Yield       
	24	Tỷ lệ cổ phiếu tự do chuyển nhượng - Free Float Percentage       
	25	Điểm Piotroski F-Score - Piotroski F-Score       
	26	Lợi thế thương mại trên tài sản - Goodwill to Assets       
	27	Lợi nhuận gộp trên tài sản - Gross Profit to Assets       
	28	Khả năng thanh toán lãi vay - Interest Coverage       
	29	Vòng quay hàng tồn kho - Inventory Turnover       
	30	Hàng tồn kho trên doanh thu - Inventory to Revenue       
	31	Nợ phải trả trên tài sản - Liabilities to Assets              
	32	Nợ dài hạn trên tài sản - Long-term Debt to Assets              
	33	Tỷ lệ giá trên giá trị sổ sách - Price-to-Book Ratio              
	34	Tỷ lệ giá trên lợi nhuận - P/E Ratio              
	35	P/E (loại trừ các khoản bất thường) - P/E              
	36	Tỷ lệ PEG - Price-Earnings-Growth Ratio              
	37	Giá trên dòng tiền tự do - Price-to-Free-Cashflow              
	38	Giá trên dòng tiền từ hoạt động kinh doanh - Price-to-Operating-Cashflow                     
	39	Khả năng dự đoán - Predictability                     
	40	Khả năng sinh lời - Profitability                     
	41	Tỷ suất sinh lợi - Rate of Return                     
	42	Tài sản hoạt động ròng đã chuẩn hóa - Scaled Net Operating Assets                     
	43	Tăng trưởng EBITDA theo năm - YoY EBITDA Growth                     
	44	Tăng trưởng EPS theo năm - YoY EPS Growth                     
	45	Tăng trưởng doanh thu theo năm - YoY Revenue Growth                            
