torch.index_select()
torch.tensor.detach().cpu().nump()

- device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')

- torch.nn.utils.clip_grad_norm_(parameters, max_norm, norm_type=2)
	- example: torch.nn.utils.clip_grad_norm_(retinanet.parameters(), 0.1)