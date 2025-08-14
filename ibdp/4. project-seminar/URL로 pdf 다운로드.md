
![[Pasted image 20250731155236.png]]
1. 브라우저에서 "Download full issue" 버튼을 클릭하면, ScienceDirect는 내부적으로 pdf-token URL을 호출. (버튼 클릭 시 호출하는 URL에 논문의 pii(논문 고유 식별자)가 리스트로 포함되어 있음)

https://www.sciencedirect.com/journal/issue/pdf-token?pii=[%22S1558787809000367%22,%22S1558787809000379%22,%22S1558787809000331%22,%22S1558787808001408%22,%22S1558787808002232%22,%22S1558787808002633%22,%22S1558787808001159%22]


![[Pasted image 20250731160438.png]]

2. token값, 각 pii를 포함해 아래 url 호출

	https://www.sciencedirect.com/science/article/pii/S1558787822000367/pdfft?token=

3. pdf 개별 다운로드