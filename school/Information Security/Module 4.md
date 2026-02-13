risk management
	The process of identifying risk, assessing its relative magnitude, and taking steps to reduce it to an acceptable level.

risk assessment
	The identification, analysis, and evaluation of risk as initial parts of risk management.

risk treatment or risk control
	The application of safeguards or controls to reduce the risks to an organization’s information assets to an acceptable level.

RM framework
	The overall structure of the strategic planning and design for the entirety of the organization’s RM efforts.

RM process
	The identification, analysis, evaluation, and treatment of risk to information assets, as specified in the RM framework.

RM Policy
- Purpose and scope
- RM intent and objectives
- Roles and responsibilities
- Resource requirements
- Risk appetite and tolerances
- RM program development guidelines
- Special instructions and revision information
- References to other key policies, plans, and guidelines

risk management (RM) plan
	A document that contains specifications for the implementation and conduct of PM efforts

residual risk
- The risk to information assets that remains even after the current controls have been applied

risk appetite
- the quantity and nature of risk that organizations are willing to accept as they evaluate the trade-offs between perfect security and unlimited accessibility 

risk tolerance
- the assessment of the amount of risk an organization is willing to accept for a particular information asset, typically synthesized into the organization's overall risk appetite

zero-tolerance risk exposure
- An extreme level of risk tolerance whereby the organization is unwilling to allow any successful attacks or suffer any loss to an information asset.


risk appetite statement
- A formal document developed by the organization that specifies its overall willingness to accept risk to its information assets, based on a synthesis of individual risk tolerances.

risk identification
- the recognition, enumeration, and documentation of risks to an organization's information assets.
	- identify the organizations information assets
	- classify them
	- categorize them into useful groups
	- prioritize them by overall importance

data classification scheme
	a formal access control methodology used to assign a level of confidentiality to an information asset and thus restrict the number of people who can access it

threat assesssment
- An evaluation of the threats to information assets, including a determination of their likelihood of occurrence and potential impact of an attack

risk analysis
- a determination of the extent to which an organizations information asset's are exposed to risk

# NIST Generic Risk Model with Key Risk Factors

![[Pasted image 20260213094116.png]]

risk evaluation
- the process of comparing an information asset's risk rating to the numerical representation of the organization's risk appetite or risk threshold to determine if risk treatment is required

mitigation risk treatment strategy
- the risk treatment strategy that attempts to eliminate or reduce any remaining uncontrolled risk through the application of additional controls and safeguards in an effort to change the likelihood of a successful attack on an information asset; also known as the defense strategy.

Three common approaches to implement the mitigation risk treatment strategy:
- Application of policy
- Application of security education training and awareness programs (SETA)
- Application of technology.

tranferren

![[Pasted image 20260213090937.png]]
- Although it might seem counterintuitive, the goal of InfoSec is not to bring residual risk to zero; rather, it is to bring residual risk in line with an organization’s risk appetite. If decision makers have been informed of uncontrolled risks and the proper authority groups within the communities of interest decide to leave residual risk in place, then the InfoSec program has accomplished its primary goal. 

![[Pasted image 20260213090946.png]]

- When a vulnerability (flaw or weakness) exists in an important asset—Implement security controls to reduce the likelihood of a vulnerability being exploited.
- When a vulnerability can be exploited—Apply layered protections, architectural designs, and administrative controls to minimize the risk or prevent the occurrence of an attack.
- When the attacker’s potential gain is greater than the costs of attack—Apply protections to increase the attacker’s cost or reduce the attacker’s gain by using technical or managerial controls. Note that the attacker’s potential gain is considered from his or her perspective, not the organization’s, so the latter’s perceived potential loss could be much smaller than the attacker’s potential gain.
- When the potential loss is substantial—Apply design principles, architectural designs, and technical and nontechnical protections to limit the extent of the attack, thereby reducing the potential for loss.
![[Pasted image 20260213091122.png]]

Cost Avoidance
- The financial savings from using the mitigation risk treatment strategy to implement a control and eliminate the financial ramifications of an incident.

Cost Benefit Analysis (CBA)
- The formal assessment and presentation of the economic expenditures needed for a particular security control, contrasted with its projected value to the organization; also known as an economic feasibility study.

Cost
- Cost of development or acquisition—Hardware, software, and services
- Training fees—Cost to train personnel
- Cost of implementation—Installing, configuring, and testing hardware, software, and services
- Service costs—Vendor fees for maintenance and upgrades or from outsourcing the information asset’s protection and/or insurance
- Cost of maintenance—Labor expense to verify and continually test, maintain, train, and update
- Potential cost from the loss of the asset—Either from removal of service (termination) or compromise by attack 

Asset valuation
- The process of assigning financial value or worth to each information asset.
	- Value retained from the cost of creating the information asset
		Value retained from past maintenance of the information asset
		Value implied by the cost of replacing the information
		Value from providing the information
		Value acquired from the cost of protecting the information
		Value to owners
		Value of intellectual property
		Value to adversaries
		Loss of productivity while the information assets are unavailable
		Loss of revenue while information assets are unavailable
		Total cost of ownership 


single loss expectancy (SLE)
	In a cost-benefit analysis, the calculated value associated with the most likely loss from an attack (impact); the SLE is the product of the asset’s value and the exposure factor.

annualized rate of occurrence (ARO)
	In a cost-benefit analysis, the expected frequency of an attack, expressed on a per-year basis.


annualized loss expectancy (ALE)
	In a cost-benefit analysis, the product of the annualized rate of occurrence and single loss expectancy.


The OCTAVE Methods
	The Operationally Critical Threat, Asset, and Vulnerability Evaluation (OCTAVE)
		The original OCTAVE Method
			Large organizations
		OCTAVE-S
			Small organizations
		OCTAVE-Allegro
			Streamlined InfoSec assessment


![[Pasted image 20260213092117.png]]

- FAIR
	- Factor Analysis of Information Risk (FAIR)
		A taxonomy for information risk
		Standard nomenclature for information risk terms
		A framework for establishing data collection criteria
		Measurement scales for risk factors
		A computational engine for calculating risk
		A modeling construct for analyzing complex risk scenarios
![[Pasted image 20260213092303.png]]
Stage 1—Identify Scenario Components
1. Identify the asset at risk.
2. Identify the threat community under consideration.
Stage 2—Evaluate Loss Event Frequency (LEF)
3. Estimate the probable Threat Event Frequency (TEF).
4. Estimate the Threat Capability (TCap).
5. Estimate Control Strength (CS).
6. Derive Vulnerability (Vuln).
7. Derive Loss Event Frequency (LEF).
Stage 3—Evaluate Probable Loss Magnitude (PLM)
8. Estimate worst-case loss.
9. Estimate probable loss.
Stage 4—Derive and Articulate Risk
10. Derive and articulate risk.

- ISO Standards for InfoSec Risk Management
![[Pasted image 20260213092640.png]]
![[Pasted image 20260213092651.png]]
- NIST Risk Management Framework (RMF)
	The National Institute of Standards and Technology (NIST)

![[Pasted image 20260213092905.png]]

![[Pasted image 20260213092918.png]]



